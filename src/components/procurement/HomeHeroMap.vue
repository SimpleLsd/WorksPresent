<template>
  <div class="map-container">
    <canvas id="canvas" ref="canvas" />
  </div>
</template>

<script setup lang="ts">
import { gsap } from 'gsap'
import { onMounted, ref } from 'vue'
import mapMotionPoints from '../../jsons/mapMotionPoints.json'

interface Point {
  x: number
  y: number
  alpha: number
}

interface Meteor {
  t: number
  alpha: number
  tail: { x: number; y: number; alpha: number }[]
}

interface Animation {
  startPoint: Point
  endPoint: Point
  controlPoint: Point
  meteor: Meteor
  curveAlpha: number
  meteorDuration: number
}

// 画布大小
const CANVAS_WIDTH = 800
const CANVAS_HEIGHT = 440

// 总动画数
const TOTAL_LINES = 5

// 颜色 RGB
const COLOR = '0, 112, 80'

// 动画速度参数
const POINT_DURATION = 0.5 // 点出现时间（秒）
const CURVE_DURATION = 0.5 // 曲线出现时间（秒）
const FADE_DURATION = 0.5 // 淡出时间（秒）
const METEOR_SPEED_FACTOR = 0.03 // 流星移动速度因子（秒/像素）

// 透明度控制参数
const POINT_MAX_ALPHA = 1 // 点最大透明度（0-1）
const CURVE_MAX_ALPHA = 0.15 // 曲线最大透明度（0-1）
const METEOR_MAX_ALPHA = 1 // 流星最大透明度（0-1）
const MIN_DISTANCE = 100 // 最小距离
const MAX_DISTANCE = 400 // 最大距离

const startPoints = mapMotionPoints.startPoints
const endPoints = mapMotionPoints.endPoints
const animations: Animation[] = []

function createAnimation(): Animation {
  let startIdx, endIdx, start, end, dx, dy, distance

  // 不断循环直到找到符合距离的点
  do {
    startIdx = Math.floor(Math.random() * startPoints.length)
    endIdx = Math.floor(Math.random() * endPoints.length)
    start = { x: startPoints[startIdx].x + 2, y: startPoints[startIdx].y + 2 }
    end = { x: endPoints[endIdx].x + 2, y: endPoints[endIdx].y + 2 }
    dx = end.x - start.x
    dy = end.y - start.y
    distance = Math.sqrt(dx * dx + dy * dy)
  } while (distance < MIN_DISTANCE || distance > MAX_DISTANCE)

  const meteorDuration = distance * METEOR_SPEED_FACTOR
  const midX = (start.x + end.x) / 2
  const midY = (start.y + end.y) / 2

  // 控制点偏移随距离增加
  const baseOffset = 100 // 基础偏移
  const distanceFactor = distance * 0.3 // 距离越长，额外增加偏移
  const totalOffset = baseOffset + distanceFactor

  const controlX = midX
  const controlY = midY + (Math.random() - 1.0) * totalOffset

  const startPoint: Point = { x: start.x, y: start.y, alpha: 0 }
  const endPoint: Point = { x: end.x, y: end.y, alpha: 0 }
  const controlPoint: Point = { x: controlX, y: controlY, alpha: 1 }
  const meteor: Meteor = { t: 0, alpha: METEOR_MAX_ALPHA, tail: [] }

  return { startPoint, endPoint, controlPoint, meteor, curveAlpha: 0, meteorDuration }
}

const canvas = ref<HTMLCanvasElement | null>(null)

onMounted(() => {
  if (!canvas.value) return
  const ctx = canvas.value.getContext('2d') as CanvasRenderingContext2D
  canvas.value.width = CANVAS_WIDTH
  canvas.value.height = CANVAS_HEIGHT

  function drawPoint(
    ctx: CanvasRenderingContext2D,
    x: number,
    y: number,
    r: number,
    alpha: number,
  ): void {
    ctx.beginPath()
    ctx.arc(x, y, r, 0, Math.PI * 2)
    ctx.fillStyle = `rgba(${COLOR}, ${alpha * POINT_MAX_ALPHA})`
    ctx.fill()
  }

  // 绘制所有 endPoints 作为背景点
  function drawBackgroundPoints() {
    endPoints.forEach((p: { x: number; y: number }) => {
      drawPoint(ctx, p.x + 2, p.y + 2, 4, 0.3) // 背景点透明度可以固定，比如 0.6
    })
  }

  function drawBezierCurve(
    ctx: CanvasRenderingContext2D,
    progress: number,
    alpha: number,
    start: Point,
    control: Point,
    end: Point,
  ): void {
    ctx.beginPath()
    ctx.moveTo(start.x, start.y)
    for (let t = 0; t <= progress; t += 0.01) {
      const x = (1 - t) ** 2 * start.x + 2 * (1 - t) * t * control.x + t ** 2 * end.x
      const y = (1 - t) ** 2 * start.y + 2 * (1 - t) * t * control.y + t ** 2 * end.y
      ctx.lineTo(x, y)
    }
    ctx.strokeStyle = `rgba(${COLOR}, ${alpha * CURVE_MAX_ALPHA})`
    ctx.lineWidth = 2
    ctx.stroke()
  }

  function drawMeteor(
    ctx: CanvasRenderingContext2D,
    t: number,
    alpha: number,
    meteor: Meteor,
    start: Point,
    control: Point,
    end: Point,
  ): void {
    const x = (1 - t) ** 2 * start.x + 2 * (1 - t) * t * control.x + t ** 2 * end.x
    const y = (1 - t) ** 2 * start.y + 2 * (1 - t) * t * control.y + t ** 2 * end.y

    meteor.tail.push({ x, y, alpha: 1 })
    if (meteor.tail.length > 600) meteor.tail.shift()

    if (meteor.tail.length > 1) {
      // 绘制彗尾
      ctx.beginPath()
      ctx.moveTo(meteor.tail[0].x, meteor.tail[0].y)
      meteor.tail.forEach((p) => ctx.lineTo(p.x, p.y))

      // 尾部线宽
      ctx.lineWidth = 2

      // 用渐变做透明衰减
      const tail = meteor.tail[0]
      const head = meteor.tail[meteor.tail.length - 1]
      const gradient = ctx.createLinearGradient(head.x, head.y, tail.x, tail.y)

      gradient.addColorStop(0, `rgba(${COLOR}, ${alpha * METEOR_MAX_ALPHA})`) // 头部亮
      gradient.addColorStop(1, `rgba(${COLOR}, 0)`) // 尾部透明

      ctx.strokeStyle = gradient
      ctx.stroke()
    }

    // 绘制彗星头部
    ctx.beginPath()
    ctx.arc(x, y, 2, 0, Math.PI * 2)
    ctx.fillStyle = `rgba(${COLOR}, ${alpha * METEOR_MAX_ALPHA})`
    ctx.fill()
  }

  function drawAll() {
    ctx.clearRect(0, 0, canvas.value!.width, canvas.value!.height)

    drawBackgroundPoints()

    animations.forEach((anim) => {
      drawPoint(ctx, anim.startPoint.x, anim.startPoint.y, 2, anim.startPoint.alpha)
      drawPoint(ctx, anim.endPoint.x, anim.endPoint.y, 2, anim.endPoint.alpha)
      drawBezierCurve(
        ctx,
        anim.curveAlpha,
        anim.curveAlpha,
        anim.startPoint,
        anim.controlPoint,
        anim.endPoint,
      )
      if (anim.meteor.t > 0 || anim.curveAlpha < 1) {
        drawMeteor(
          ctx,
          anim.meteor.t,
          anim.meteor.alpha,
          anim.meteor,
          anim.startPoint,
          anim.controlPoint,
          anim.endPoint,
        )
      }
    })
  }

  function startAnimation(anim: Animation) {
    const timeline = gsap.timeline({
      onComplete: () => {
        const index = animations.indexOf(anim)
        if (index !== -1) {
          animations.splice(index, 1)
          const newAnim = createAnimation()
          animations.push(newAnim)
          startAnimation(newAnim)
        }
      },
      onUpdate: drawAll,
    })

    timeline
      .to([anim.startPoint, anim.endPoint], { alpha: 1, duration: POINT_DURATION })
      .to(anim, { curveAlpha: 1, duration: CURVE_DURATION })
      .to(anim.meteor, { t: 1, duration: anim.meteorDuration, ease: 'sine.inOut', yoyoEase: true })
      .to([anim.startPoint, anim.endPoint, anim, anim.meteor], {
        alpha: 0,
        curveAlpha: 0,
        duration: FADE_DURATION,
      })
  }

  for (let i = 0; i < TOTAL_LINES; i++) {
    const anim = createAnimation()
    animations.push(anim)
    startAnimation(anim)
  }

  // 初始绘制
  drawAll()
})
</script>

<style scoped>
.map-container {
  width: 800px;
  height: 440px;
  background-image: url(../../assets/map_bg.png);
  background-size: cover;
  background-position: center;
  position: relative;
}
canvas {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: transparent;
}
</style>

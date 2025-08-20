<template>
  <div class="container">
    <div class="main">
      <img src="../../assets/imgs/procurement/bg_hero.png" alt="" />
      <div class="hero_info">
        <div class="banner">
          <div class="banner_1">
            <h3 class="title">連結政府與企業的橋樑</h3>
            <p class="des">
              澳門特別行政區政府誠邀本地企業加入中央供應商資料庫，共享政府採購商機，促進澳門經濟繁榮發展。加入資料庫是參與諮詢程序、直接磋商程序的必要資格。
            </p>
          </div>
        </div>
        <div class="button_group">
          <button class="main_button">立即入庫</button>
          <a class="text_link">點解要入庫</a>
          <a class="text_link">最新公告</a>
          <a class="text_link">招標資訊</a>
        </div>
      </div>
      <div class="map_container">
        <HomeHeroMap />
      </div>
      <div class="right_blue"></div>
    </div>
    <div class="num_infos">
      <div class="info">
        <div class="line_1">
          <p class="num">31,415</p>
          <p class="suffix">個</p>
        </div>
        <p class="line_2">已入庫供應商</p>
      </div>
      <div class="info">
        <div class="line_1">
          <p class="num">31,415</p>
          <p class="suffix">個</p>
        </div>
        <p class="line_2">已入庫供應商</p>
      </div>
      <div class="info">
        <div class="line_1">
          <p class="num">31,415</p>
          <p class="suffix">個</p>
        </div>
        <p class="line_2">已入庫供應商</p>
      </div>
      <div class="info">
        <div class="line_1">
          <p class="num">31,415</p>
          <p class="suffix">個</p>
        </div>
        <p class="line_2">已入庫供應商</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import HomeHeroMap from './HomeHeroMap.vue'
</script>

<style scoped>
.container {
  width: 100%;
  height: 440px;
  overflow: hidden;
  background-color: #fff;
}
.main {
  display: flex;
  width: 1100px;
  height: 100%;
  align-items: center;
  position: relative;
  margin: 0 auto;
}
.main img {
  width: 1440px;
  height: 440px;
  position: absolute;
  left: calc((1100px - 1440px) / 2);
  bottom: 0;
  z-index: 1;
}
.hero_info {
  width: 520px;
  height: 100%;
  padding-top: 80px;
  z-index: 3;
}
.hero_info .banner .banner_1 {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.hero_info .banner .banner_1 .title {
  font-size: 44px;
  line-height: 62px;
  font-weight: 500;
  color: #303133;
}
.hero_info .banner .banner_1 .des {
  font-size: 16px;
  line-height: 28px;
  font-weight: 400;
  color: #606266;
}
.hero_info .button_group {
  margin-top: 24px;
  display: flex;
  gap: 20px;
  flex-direction: row;
  align-items: center;
}
button.main_button {
  display: flex;
  width: 150px;
  height: 48px;
  justify-content: center;
  align-items: center;
  gap: 4px;
  border-radius: 100px;
  background: #ffc107;
  border: none;
  color: #000;
  font-size: 14px;
  font-weight: 500;
}
a.text_link {
  font-size: 14px;
  color: #000;
  font-weight: 400;
}
.map_container {
  width: 800px;
  height: 440px;
  z-index: 2;
  position: absolute;
  right: -110px;
}
.right_blue {
  background-color: #d4e9ed;
  height: 440px;
  width: 100vw;
  right: -100vw;
  position: absolute;
}
</style>

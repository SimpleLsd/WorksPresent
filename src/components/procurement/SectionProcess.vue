<template>
  <div class="container">
    <div class="main">
      <section-title icon-name="2_progress.svg" title="入庫流程" :view-more="false" />
      <div class="progress home_shadow home_border r">
        <div class="step_group">
          <img src="../../assets/imgs/procurement/icon_progress_1.svg" alt="" />
          一戶通/商社通登入
        </div>
        <img src="../../assets/imgs/procurement/icon_progress_arrow.png" alt="" />
        <div class="step_group">
          <img src="../../assets/imgs/procurement/icon_progress_2.svg" alt="" />
          填寫企業資料
        </div>
        <img src="../../assets/imgs/procurement/icon_progress_arrow.png" alt="" />
        <div class="step_group">
          <img src="../../assets/imgs/procurement/icon_progress_3.svg" alt="" />
          選擇供應商分類目錄
        </div>
        <img src="../../assets/imgs/procurement/icon_progress_arrow.png" alt="" />
        <div class="step_group">
          <img src="../../assets/imgs/procurement/icon_progress_4.svg" alt="" />
          補充相關資料
        </div>
        <img src="../../assets/imgs/procurement/icon_progress_arrow.png" alt="" />
        <div class="step_group">
          <img src="../../assets/imgs/procurement/icon_progress_5.svg" alt="" />
          提交即時自動審核入庫
        </div>
        <img src="../../assets/imgs/procurement/icon_progress_arrow.png" alt="" />
        <div class="step_group">
          <img src="../../assets/imgs/procurement/icon_progress_6.svg" alt="" />
          即可參與政府採購活動
        </div>
      </div>
      <div class="button_group">
        <button class="main_button home_shadow">立即入庫</button>
        <span>平均5分鐘即可完成入庫登記</span>
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
import SectionTitle from './SectionTitle.vue'
</script>
<style scoped>
.container {
  width: 100%;
  background-color: #fff;
  /* background-color: var(--procurement-bg); */
}
.main {
  width: 1100px;
  /* height: 300px; */
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 40px;
  align-items: center;
  margin: 0 auto;
  padding: 80px 0;
}
.progress {
  width: 100%;
  height: 150px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0 36px;
}
.step_group {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: var(--text-primary);
  font-size: 14px;
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
.button_group {
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 12px;
}
.button_group span {
  display: flex;
  align-items: center;
  gap: 4px;
  line-height: 24px;
  font-size: 14px;
  color: var(--text-secondary);
}
.button_group span::before {
  display: inline-block;
  content: '';
  width: 16px;
  height: 16px;
  background: url('../../assets/imgs/procurement/icon_progress_done.svg');
  flex-shrink: 0;
}
</style>

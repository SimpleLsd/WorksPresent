<template>
  <div class="container">
    <div class="main">
      <section-title icon-name="3_notice.svg" title="最新公告" :view-more="true" />
    </div>
    <div class="notice_group">
      <div class="notice_card">
        <div class="info_group">
          <div class="tag">
            <span>累目新增</span>
          </div>
          <span class="date">2025-08-18</span>
        </div>
        <div class="title">新增「低碳设备维护」与「无障碍设施改造」品类</div>
        <div class="des">歡迎本地供應商加入該品類，拓展綠色與無障礙項目能力。</div>
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
  background-color: var(--procurement-bg);
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
</style>

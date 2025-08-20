<template>
  <div class="container">
    <div class="main">
      <a class="tab">
        首頁
        <div class="active"></div>
      </a>
      <a class="tab">登記入庫</a>
      <a class="tab">供應商分類目錄</a>
      <a class="tab">通知公告</a>
      <a class="tab">諮詢標公告</a>
      <a class="tab">法律法規</a>
      <a class="tab">常見問題</a>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  height: 50px;
  background-color: #107246;
}
.main {
  display: flex;
  width: 1100px;
  align-items: center;
  margin: 0 auto;
}
.tab {
  height: 50px;
  display: flex;
  padding: 0 16px;
  position: relative;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-size: 14px;
}
.tab:hover {
  cursor: pointer;
  background-color: #ffffff10;
  transition: 150ms ease-out;
}
.active {
  width: 16px;
  height: 4px;
  background-color: #ffc107;
  position: absolute;
  margin: auto;
  bottom: 0;
}
</style>

<template>
  <header>
    <div class="main">
      <div class="logo_group">
        <img src="../../assets/imgs/procurement/icon_MACAU_GOV.svg" />
        <div class="gov_texts">
          <p class="top">澳門特別行政區政府</p>
          <p class="bottom">中央供應商資料庫</p>
        </div>
      </div>
      <div class="right_group">
        <div class="search">
          <img src="../../assets/imgs/procurement/icon_main_search.svg" alt="" />
          <input type="text" placeholder="搜索供應商分類、公告..." />
        </div>
        <img src="../../assets/imgs/procurement/icon_header_i18n.svg" />
        <button>
          <img src="../../assets/imgs/procurement/icon_header_user.svg" alt="" />
          登入
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
header {
  width: 100%;
  height: 80px;
  background-color: #004f38;
}
.main {
  margin: 0 auto;
  width: 1100px;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.logo_group {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 8px;
}
.gov_texts {
  display: flex;
  gap: 4px;
  height: 100%;
  flex-direction: column;
}
.gov_texts .top {
  font-size: 12px;
  opacity: 0.8;
  color: #fff;
}
.gov_texts .bottom {
  font-size: 16px;
  line-height: 22px;
  color: #fff;
}
.right_group {
  display: flex;
  align-items: center;
  gap: 20px;
}
.right_group .search {
  display: flex;
  width: 240px;
  height: 40px;
  padding: 0 12px;
  align-items: center;
  gap: 8px;
  border-radius: 100px;
  background: rgba(255, 255, 255, 0.95);
}
.right_group input {
  border: none;
  height: 100%;
  width: 216px;
  background: none;
}
.right_group input:focus {
  outline: none;
}
.right_group input::placeholder {
  color: #004f38;
}
.right_group button {
  display: flex;
  width: 100px;
  padding: 10px;
  justify-content: center;
  align-items: center;
  gap: 4px;
  border-radius: 100px;
  background: #ffc107;
  border: none;
  color: #004f38;
}
</style>

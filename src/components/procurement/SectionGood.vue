<template>
  <div class="container">
    <div class="main">
      <div class="num_cards">
        <div class="num_card home_shadow home_border r">
          <div class="num_group">
            <div class="num">31,514</div>
            <div class="suffix">萬</div>
          </div>
          <div class="des">已入庫供應商</div>
        </div>
        <div class="num_card home_shadow home_border r">
          <div class="num_group">
            <div class="num">92</div>
            <div class="suffix">個</div>
          </div>
          <div class="des">本月新入庫</div>
        </div>
        <div class="num_card home_shadow home_border r">
          <div class="num_group">
            <div class="num">65,358</div>
            <div class="suffix">萬</div>
          </div>
          <div class="des">本年諮詢標採購額</div>
        </div>
        <div class="num_card home_shadow home_border r">
          <div class="num_group">
            <div class="num">9,793</div>
            <div class="suffix">萬</div>
          </div>
          <div class="des">本年諮詢標數量</div>
        </div>
      </div>
      <!-- 标题位置 -->
      <section-title icon-name="1_good.svg" title="登記成為中央供應商的好處" :view-more="false" />
      <div class="goods">
        <div class="good home_shadow home_border r">
          <div class="title_group">
            <h4>生意機會豐富</h4>
            <img src="../../assets/imgs/procurement/illu_good_1.svg" alt="" class="illu" />
          </div>
          <div class="info_group">
            <div class="des">
              入庫即有機會參與澳門政府各類諮詢程序及直接磋商程序的採購項目，從辦公用品到專業服務，多元化商機等您發掘。
            </div>
            <a href="" class="link">了解政府探購品目</a>
          </div>
        </div>
        <div class="good home_shadow home_border r">
          <div class="title_group">
            <h4>一站式入庫</h4>
            <img src="../../assets/imgs/procurement/illu_good_2.svg" alt="" class="illu" />
          </div>
          <div class="info_group">
            <div class="des">
              非政府債務人且經營中的澳門企業、社團財團、自由職業者，線上交資料即可入庫。入庫後可被所有政府部門檢索與遴選。
            </div>
            <a href="" class="link">了解政府探購品目</a>
          </div>
        </div>

        <div class="good home_shadow home_border r">
          <div class="title_group">
            <h4>公平遴選</h4>
            <img src="../../assets/imgs/procurement/illu_good_3.svg" alt="" class="illu" />
          </div>
          <div class="info_group">
            <div class="des">
              政府採購咨詢程序，採用完全隨機及一次性遴選機制篩選供應商，避免人為挑選，兼顧公正與效率。
            </div>
            <a href="" class="link">了解政府探購品目</a>
          </div>
        </div>
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
  /* height: 440px; */
  /* overflow: hidden; */
  background-color: #fff;
  background-color: var(--procurement-bg);
}
.main {
  width: 1100px;
  /* height: 100%; */
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 40px;
  align-items: center;
  margin: 0 auto;
  padding: 108px 0 80px 0;
}
.num_cards {
  position: absolute;
  top: -70px;
  width: 1100px;
  height: 140px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  gap: 20px;
  z-index: 2;
  /*  */
  /* background-color: #eee; */
  /* background-color: var(--procurement-bg); */
}
.num_card {
  flex: 1;
  height: 100%;
  background: rgba(255, 255, 255, 0.95);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.num_group {
  display: flex;
  flex-direction: row;
  /* justify-content: baseline; */
  align-items: baseline;
  gap: 8px;
}
.num_card .num {
  font-size: 32px;
  font-weight: 600;
  color: #107246;
}
.num_card .suffix {
  font-size: 14px;
  font-weight: 600;
  color: #107246;
}
.num_card .des {
  font-size: 14px;
  font-weight: 400;
  color: #909399;
}
.num_card .num,
.num_card .suffix {
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.25);
}

.goods {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  gap: 24px;
}
.good {
  /* width: 350px; */
  flex: 1;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 0;
}
.good .title_group {
  width: 100%;
  height: 64px;
  background: linear-gradient(180deg, #fffcf1 0%, rgba(255, 252, 241, 0) 100%);
  position: relative;
}
.good .title_group h4 {
  position: absolute;
  top: 20px;
  left: 20px;
  font-size: 24px;
  font-weight: 600;
  color: #303133;
}
.good .title_group .illu {
  position: absolute;
  right: 0;
  bottom: 0;
}
.good .info_group {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 16px;
  gap: 16px;
  background-color: var(--text-white);
}
.good .info_group .des {
  color: var(--text-primary);
  font-size: 14px;
  font-weight: 400;
  line-height: 28px; /* 200% */
}
.good .info_group .link {
  color: #107246;
  font-size: 14px;
  font-weight: 400;
  line-height: 28px; /* 200% */
  text-align: center;
}
</style>

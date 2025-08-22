<template>
  <div class="container">
    <img :src="iconUrl" alt="" />
    <h3>{{ title }}</h3>
    <a v-if="viewMore" class="view_more">
      查看更多
      <img src="../../assets/imgs/procurement/icon_section_title_more.svg" alt="" />
    </a>
  </div>
</template>
<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  iconName: string
  title: string
  viewMore: boolean
}

const props = defineProps<Props>()

const iconUrl = computed(() => {
  // ../../assets/imgs/procurement/icon_section_title_1_good.svg
  return `/src/assets/imgs/procurement/icon_section_title_${props.iconName}`
})
</script>
<style scoped>
.container {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  transition: 250ms ease-out;
}
.container h3 {
  flex: 1;
  font-size: 32px;
  color: #303133;
  font-weight: 600;
}
.view_more {
  display: flex;
  align-items: center;
  gap: 4px;
  color: var(--text-secondary);
  transition: color 200ms ease-out;
  cursor: pointer;
}
.view_more:hover {
  color: var(--text-primary);
}
</style>

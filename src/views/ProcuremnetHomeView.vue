<template>
  <div class="main">
    <general-header />
    <general-tab />
    <home-hero />
  </div>
</template>

<script lang="ts" setup>
import GeneralHeader from '@/components/procurement/GeneralHeader.vue'
import GeneralTab from '@/components/procurement/GeneralTab.vue'
import HomeHero from '@/components/procurement/HomeHero.vue'
</script>

<style scoped>
.main {
  width: 100%;
  height: 100%;
  background-color: #fff;
}
</style>

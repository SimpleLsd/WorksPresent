<template>
  <div class="home_main">
    <general-header />
    <general-tab />
    <home-hero />
    <section-good />
    <section-process />
    <SectionNotice />
  </div>
</template>

<script lang="ts" setup>
import GeneralHeader from '@/components/procurement/GeneralHeader.vue'
import GeneralTab from '@/components/procurement/GeneralTab.vue'
import HomeHero from '@/components/procurement/HomeHero.vue'
import SectionGood from '@/components/procurement/SectionGood.vue'
import SectionProcess from '@/components/procurement/SectionProcess.vue'
import SectionNotice from '@/components/procurement/SectionNotice.vue'
</script>

<style>
.home_main {
  width: 100%;
  height: 100%;
  background-color: #fff;
}
.home_shadow {
  box-shadow: var(--home-shadow);
}
.home_border {
  border: var(--home-border);
}
.r {
  border-radius: var(--home-r);
}
</style>

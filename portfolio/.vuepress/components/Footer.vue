<template>
  <span class="text">{{ $site.themeConfig.footer }} - {{ new Date().getFullYear() }}</span>
</template>

<style scoped>
  .text {
    display: block;
    font-size: 0.8rem;
    margin-top: auto;
    text-align: center;
    padding: 4rem 5vw;
  }
</style>

<template>
  <div>
    <df-header></df-header>
    <nuxt></nuxt>
    <df-footer></df-footer>
  </div>
</template>

<script>
import DfFooter from '~components/Footer.vue'
import DfHeader from '~components/Header.vue'
export default {
  components: {
    DfHeader,
    DfFooter
  }
}
</script>

<style>
  .container {
    margin: 0;
    width: 100%;
    min-height: 100%;
    padding-bottom: 140px;
  }
</style>

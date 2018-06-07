<template>
  <div class="loader" v-show="hasLoading"></div>
</template>

<script>
export default {
  props: ['hasLoading']
}
</script>

<style scoped>
  .loader {
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    background-color: #fff;
  }

  .loader:after {
    content: '';
    width: 50px;
    height: 50px;
    position: fixed;
    top: 50%;
    left: 50%;
    border: 8px solid #f3f3f3;
    border-top: 8px solid #7A9CCF;
    border-radius: 50%;
    animation: spin 2s linear infinite;
  }

  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
</style>


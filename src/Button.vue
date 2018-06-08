<template>
  <a :href="linkTo" target="_blank" class="btn" :class="className">
    <slot></slot>
  </a>
</template>

<script>
export default {
  props: ['className', 'linkTo']
}
</script>

<style scoped>
  .btn {
    border: 0;
    box-sizing: border-box;
    padding: .5em;
    color: #fff;
    text-decoration: none;
    transition: all .3s;
  }

  .btn:hover {
    cursor: pointer;
    transform: translateY(-3px);
  }

  .info {
    background-color: #7A9CCF;
  }

  .danger {
    background-color: tomato;
  }
</style>

<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "tabBar"
  }
</script>

<style scoped>
  @import '../../../assets/css/base.css';


  #tab-bar {
    display: flex;
    position: fixed;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: #f6f6f6;
    box-shadow: 0 -3px 1px rgba(100,100,100,0.2);
  }


</style>

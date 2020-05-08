<template>
    <div class="tab-bar-item" @click="itemClick">
      <!--需要动态生成，所以定义的时候，就需要定义上具名的slot-->
      <div v-if="!isActive">
        <slot name="item-icon"></slot>
      </div>
      <div v-else>
        <slot name="item-icon-active"></slot>
      </div>
      <div :style="activeStyle">
        <slot name="item-text"></slot>
       <!-- <slot :class='{active:isActive}' name="item-text"></slot>-->
      </div>
    </div>
</template>

<script>
  export default {
    name: "tabBarItem",
    data() {
      return {
       /* isActive: false*/
      }
    },
    computed: {
      isActive() {
        return this.$route.path.indexOf(this.path) !== -1
      },
      activeStyle() {
        return this.isActive? {color: this.activeColor} : {}
      }
    },
    props:{
      path: String,
      activeColor: {
        type: String,
        default: 'red'
      }
    },
    methods: {
      itemClick() {
        this.$router.push(this.path)
      }
    }
  }
</script>

<style scoped>
  .tab-bar-item {
    flex: 1;
    height: 49px;
    text-align: center;
    font-size: 14px;
  }

  .tab-bar-item img {
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }

/*  .active {
    color: red;
  }*/
</style>

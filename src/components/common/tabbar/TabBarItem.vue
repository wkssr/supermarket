<template>
  <div id="tab-bar-item" @click="itemClick">
    <div class="item-icon" v-show="!isActive"><slot name="icon"></slot></div>
    <div class="item-active-icon" v-show="isActive"><slot name="active-icon"></slot></div>
    <div class="item-text" :style="activeStyle"><slot name="text"></slot></div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: String,
    activeColor: {
      type: String,
      default: 'red'
    }
  },
data() {
  return {
    // isActive:false
  }
},
computed: {
  isActive() {
    return this.$route.path.indexOf(this.path) !== -1
  },
  activeStyle() {
    return this.isActive ? {color: this.activeColor} : {}
  }
},
methods: {
    itemClick() {
     this.$router.replace(this.path)
    
    }
  }
}
</script>

<style>
#tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
#tab-bar-item img {
  height: 24px;
  width: 24px;
  margin-top: 3px;
    /* 去除图片底部默认像素 */
  vertical-align: middle;  
  margin-bottom: 2px;

}
.active {
  color: red;
}
</style>
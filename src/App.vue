<template>
  <div id="app">
    <div class="tab1" ref="tab1">
      <ul  class="wrapper1" ref="wrapper">
        <li v-for="(item,index) in 100" class="tabitem1" ref="tabitem1" :key="index">{{item}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  props: {
    /** * 是否开启横向滚动 */ scrollX: { type: Boolean, default: true }
  },
  name: 'App',
  created () {
    this.$nextTick((res) => {
      this.initScrollH()
    })
  },
  methods: {
    initScrollH () {
      if (!this.scrolln) {
        this.$nextTick(() => {
          this.scrolln = new Bscroll(this.$refs.tab1, {
            startX: 0,
            click: true,
            scrollX: false
          })
          console.log(this.scrolln)
        })
      } else {
        this.scrolln.refresh()
      }
    }
  }
}
</script>

<style>
body,
html {
  height: 100%;
}
ul li {
  list-style: none;
}
.tab1{
  height: 100vh;
  position: relative;
}
.wrapper1 {
  position: absolute;
  padding:0;
  width:100vw;
}
.tabitem1 {
  width:40px;
  background: yellow;
}
</style>

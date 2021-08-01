<template>
  <div class="about">
    <h1>This is an about page</h1>
    <ul class="flex">
      <scroll-num
        v-for="(item, index) of numArr"
        :key="index"
        as="li"
        :i="item"
        :delay="index + 1"></scroll-num>
    </ul>
    <div class="logo-view">
      <img class="image" src="./../assets/logo.png" alt="">
    </div>
    <div class="varText" :style="{'--varCSS': varCss}">
      <div class="text-view">变色</div>
      <button @click="handleClick">bianse</button>
    </div>
  </div>
</template>

<script>
import ScrollNum from './../components/ScrollNumber.vue'
export default {
  components: {
    ScrollNum
  },
  data() {
    return {
      num: 886,
      varCss: '#ccc',
    }
  },
  computed: {
    numArr() {
      const str = String(this.num)
      let arr = []

      for (let i = 0; i < str.length; i++) {
        arr.push(parseInt(str[i]))
      }

      return arr
    }
  },
  mounted() {
    setInterval(() => this.num ++, 5000)
  },
  methods: {
    // 动态设置 css 变量，改变它的值
    handleClick() {
      this.varCss = '#666'
    }
  }
}
</script>

<style scoped>
.flex {
  display: flex;
}
ul {
  padding: 0;
  margin: 0;
  list-style: none;
}
.logo-view {
  background: #ccc;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  overflow: hidden;
}
.logo-view .image {
  width: 100%;
  height: 100%;
}
.logo-view .image:hover {
  transform: rotate(666turn);
  transition-delay: 1s;
  transition-property: all;
  transition-duration: 59s;
  transition-timing-function: cubic-bezier(0.34, 0, 0.84, 1);
}

.text-view {
  height: 20px;
  color: var(--varCSS);
}
</style>
<template>
  <div class="navbar">
    <div class="title_g bolid_g tarbar_item "  @click="handleClick">项目详情</div>
    <div class="title_g bolid_g tarbar_item " :class="" @click="comeBack">支持列表</div>
      <div class="line" :class="animate"></div>
  </div>
</template>

<script>
export default {
  name: 'navbar',
  data () {
    return {
      a1: true,
      a2: false
    }
  },
  computed: {
    animate () {
      if (this.a1) return 'animtion1'
      if (this.a2) return 'animtion2'
      return ''      
    }
  },
  methods: {
    handleClick () {
      this.a2 = false
      console.log('click')
      this.a1 = true
    },
    comeBack () {
      this.a1 = false
      this.a2 = true
    }
  }
}
</script>

<style  scoped>
.navbar{
  display: flex;
}
.tarbar_item{
  width: 100px;
}
.line{
  border-top: 3px solid #0398e7;
  width: 100px;
}
.animtion1{
  animation: slide 1s;  
  animation-fill-mode: forwards;
}

.animtion2{
  animation: slide_back 1s;  
  animation-fill-mode: forwards;
}

@keyframes slide {
  0% {
    transform: translateX(0)
  }
  100% {
    transform: translateX(100px)
  }
}

@keyframes slide_back {
  0% {
    transform: translateX(100px)
  }
  100% {
    transform: translateX(0px)
  }
}
</style>

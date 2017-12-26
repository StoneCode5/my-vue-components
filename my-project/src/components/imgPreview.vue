<!-- 对于微信九宫格的图片居中显示处理 -->

<style scoped>
  .imgWrapper{
    width: 100vw;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.82);
    /* opacity: 0.8;  opacity会把其子元素变透明 */
    /* z-index: 10; */
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .img {
    max-width:1080px;
    max-height:720px;
  }
</style>
<template>
  <div class="imgPreview" v-show="visible">
    <div class="imgWrapper" @click="closeWrapper">
      <img :src="imgUrl" alt="" class="img">
    </div>
  </div>
</template>

<script>



export default {
  data () {
    return {
      wrapperVisible: false
    }
  },
  props: {
    visible:{
      default:false
    },
    imgUrl: {
      default: '' 
    }
  },
  watch: {
    visible (val) {
      console.log('this',  document.body)
      document.body.appendChild(this.$el)
    }
  },
  mounted() {
    
  },
  methods: {
    closeWrapper() {
      this.$emit('update:visible', false)
    }
  }
}
</script>



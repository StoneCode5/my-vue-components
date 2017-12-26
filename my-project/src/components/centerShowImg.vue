<!-- 对于微信九宫格的图片居中显示处理 -->

<style scoped>
  .imgBox{
    display: flex;
    flex-wrap: wrap;
  }
  .imgItemBox{
    width:50vw;
    height:50vw;
    overflow: hidden;
  }
  /* 如果不考虑兼容性,可以直接使用object-fit:cover;来达到效果.*/
  /* .imgItem{
    width: 100%; height: 100%;    
    object-fit: cover;
  } */

</style>
<template>
  <div class="centerShowImg">
    <div class="imgBox">
      <div class="imgItemBox" v-for="(item, index) in data" :key="index" @click="lookDetail(item.url)">
        <img :src="item.url" alt="" class="imgItem" ref="imgList">
      </div>
    </div>
    <imgPreview :visible.sync="isPreview" :imgUrl="imgDetailUrl"></imgPreview>
  </div>
</template>

<script>
import imgPreview from './imgPreview'
export default {
  data () {
    return {
      imgArr: [
      ],
      isPreview: false,
      imgDetailUrl: ''
    }
  },
  components: {
    imgPreview
  },
  props: {
    data:{
      default:[
        {url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1514269362763&di=cbdc9b8564041a075898a69c1250a3c4&imgtype=0&src=http%3A%2F%2Fimgstore.cdn.sogou.com%2Fapp%2Fa%2F100540002%2F604382.jpg'},
        {url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1514276975248&di=ea6c6656245e62a87e7c2cbb538a03ae&imgtype=0&src=http%3A%2F%2Fuploads.xuexila.com%2Fallimg%2F1706%2F28-1F62Q22313.jpg'}
      ]
    }
  },

  mounted() {
    const that = this
    let imgList = this.$refs.imgList
    imgList.forEach(function (v) {
        v.onload = function () {
          that.updateImgPosition(v)   
        } 
      })
  },
  methods: {
    updateImgPosition (v) {
      let imgWidth = v.width
      let imgHeight = v.height
      let imgBoxWidth = window.innerWidth * 0.25 // window.innerWidth是可视窗口的宽度.
      let imgBoxHeight = imgBoxWidth
      if (imgWidth > imgHeight) {
        v.style.height = '100%'
        let heightRate = (imgBoxHeight / imgHeight)
        let leftNum = ((imgWidth * heightRate) - imgBoxWidth) / 2
        v.style.margin = `0 0 0 ${-leftNum}px`
      } else if (imgWidth < imgHeight) {
        v.style.width = '100%'
        let widthRate = (imgBoxWidth / imgWidth)
        let topNum = ((imgHeight * widthRate) - imgBoxHeight) / 2
        v.style.margin = `${-topNum}px 0 0 0 `
      } else if (imgWidth === imgHeight) {
        v.style.width = '100%'
        v.style.height = '100%'
      }
    },

    lookDetail (imgUrl) {
      console.log('clicked')
      let height = window.innerHeight
      document.body.style = `height: ${height}px; overflow-y: hidden;`
      this.isPreview = true
      this.imgDetailUrl  = imgUrl
    }
  }
}
</script>



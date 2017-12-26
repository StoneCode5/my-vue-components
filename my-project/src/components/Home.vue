<template>
  <div class="home">
    <centerShowImg :data="imgData"></centerShowImg>
  </div>
</template>

<script>
import centerShowImg from './centerShowImg'
export default {
  name: 'home',
  data () {
    return {
      imgData:[
        {url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1514269362763&di=cbdc9b8564041a075898a69c1250a3c4&imgtype=0&src=http%3A%2F%2Fimgstore.cdn.sogou.com%2Fapp%2Fa%2F100540002%2F604382.jpg'},
        {url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1514269362763&di=cbdc9b8564041a075898a69c1250a3c4&imgtype=0&src=http%3A%2F%2Fimgstore.cdn.sogou.com%2Fapp%2Fa%2F100540002%2F604382.jpg'},
        {url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1514269362763&di=cbdc9b8564041a075898a69c1250a3c4&imgtype=0&src=http%3A%2F%2Fimgstore.cdn.sogou.com%2Fapp%2Fa%2F100540002%2F604382.jpg'},
        {url: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1514276975248&di=ea6c6656245e62a87e7c2cbb538a03ae&imgtype=0&src=http%3A%2F%2Fuploads.xuexila.com%2Fallimg%2F1706%2F28-1F62Q22313.jpg'}
      ]
    }
  },
  components: {
    centerShowImg
  }
}
</script>

<style scoped>

</style>

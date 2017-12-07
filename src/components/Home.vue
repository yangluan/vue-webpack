<template>
  <div id="home">
    <div class="loginAnimat" id="loginAnimat"></div>
    <div class="show">
          <div class="swiper-slide"><img src="./images/banner/timg.jpg" alt="" id="imgfirst"></div>
      <div class="userPalyRoom">
        <div v-for="item in firstArr" :key="firstArr.item">
          <span class="toumingCen"><span class="bgc1" id="bgc1" v-if="item.Device.deviceStatus"></span><span id="wxz1"></span></span>
          <span class="toumingcen2"><span class="bgc2" id="bgc2"></span><span id="wxz2"></span></span>
          <div><img :src="imgUrl+item.Product.PicUrl" alt="" class="picLoco"></div>
          <p>{{item.Product.Name}}</p>
          <p><span><img src="./images/coin.png" alt=""></span><span>  <span>{{item.Product.Price}}</span>币/次</span></p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default{
    name: 'home',
    data () {
      return {
        firstArr: [],
        imgUrl: 'http://zhuawawa-cdn.hljoy.com/1.0.4/',
        status: 'ready'
      }
    },
    created: function () {
      this.$ajax.get('http://zhuawawa-debug.hljoy.com/api/1.0.4/play/GetRoomList/0/Id/Name/Device/Product/?token=10004:1512099830:0af71dc955a2b146fbd93ab6d84900b1').then(response => {
        this.firstArr = response.data.data
        console.log(this.firstArr)
      })
    },
    methods: {},
    computed: {}
  }
</script>


<style lang="scss" scoped="" type="text/css">
  .bgc1{
    width: .5rem;
    height: .5rem;
    position: absolute;
    left: 1.5rem;
    top: .25rem;
    border-radius: 50%;
    background-color: green;
  }
  .bgc2{
    width: .5rem;
    height: .5rem;
    position: absolute;
    left: 1.5rem;
    top: .25rem;
    border-radius: 50%;
    background-color: green;
  }
  .toumingCen{
    width: 5.8rem;
    top: 17rem;
    left: 1.16rem;
    height: 1rem;
    position: absolute;
    background-color: white;
    opacity: .5;
  }
  .toumingcen2{
    width: 5.8rem;
    top: 17rem;
    left: 9.26rem;
    height: 1rem;
    position: absolute;
    background-color: white;
    opacity: .5;
  }
  .picLoco{
    width: 6rem;
    height: 6rem;
  }
  .show {
    flex-grow: 1;
    background-color: #AFD3F7;
    padding-top: 3.41333rem;
    padding-bottom: 3.2rem;
    font-size: 20px; }
  #imgfirst{
    width: 100%;
    height:9rem;
  }
  .show .userPalyRoom {
    width: 100%;
    display: flex;
    justify-content: space-between; }
  .show .userPalyRoom div {
    text-align: center;
    font-size: 0.32rem;
    margin: 0.21333rem;
    width: 7.68rem;
    height: 7.68rem; }
  .show .userPalyRoom div span {
    display: inline-block; }
  .show .userPalyRoom div span img {
    width: 0.74667rem;
    height: 0.74667rem; }
  .show .userPalyRoom div div {
    width: 6.4rem;
    height: 6.4rem;
    border: 1px solid transparent;
    margin: auto;
    background-image: url("./images/product_frame.png");
    -webkit-background-size: 6.4rem 6.4rem; }
.loginAnimat{
  width:100%;
  display: none;
  z-index: 9;
  height: 28.5rem;
  background-color: red;
  background-image: url('./images/splash_bg.png');
  -webkit-background-size:100% 28.5rem;
  position: fixed;;
}
</style>

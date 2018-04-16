<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <keep-alive>
      <router-view :seller="seller"></router-view>
    </keep-alive>
  </div>
</template>


<script>
import header from './components/header/header.vue'
// data返回状态码
const ERR_OK = 0

export default {
  data () { return { seller: { 'foo': 42 } } },
  created () {
  this.$http.get('/api/seller').then(res => {
      if (res.data.errno === ERR_OK) {
        this.seller = res.data.data
        console.log(this.seller)
      }
    })
  },
  components: {
 'v-header': header
  }
}
function hello () {
 console.log(123)
}
hello()
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  /*-webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;*/
  color: #2c3e50;
/*  text-align: center;
  margin-top: 60px;*/
}
.tab{
	display: flex;
	width: 100%;
	height: 40px;
	line-height: 40px;
	border-bottom: 0.02rem solid rgba(7, 17, 27, 0.1);

}
.tab-item{
	flex:1;
	text-align: center;
}
a{
	display: block;
	font-size: 14px;
	color: rgb(77,85,93);
	
}
a.active{
	color: rgb(240, 20, 20);
}

</style>

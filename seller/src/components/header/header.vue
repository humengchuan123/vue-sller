<template>
<div class="header">
  <div class="content-wrapper">
    <div class="avatar">
      <img  :src="seller.avatar">
    </div>
    <div class="content">
      <div class="title">
        <span class="brand"></span>
        <span class="name">{{seller.name}}</span>
      </div>
      <div class="description">
        {{seller.description}}/{{seller.deliveryTime}}分钟送达
      </div>
      <div v-if="seller.supports" class="supports">
        <span class="icon" :class="classMap[seller.supports[0].type]"></span>
        <span class="text">{{seller.supports[0].description}}</span>
      </div>
    </div>
    <div v-if="seller.supports" class="supports-count">
    	<span class="count">{{seller.supports.length}}个</span>
    	<i class="icon-arrow_right">></i>
    </div>
  </div>
  <div class="bulletin-wrapper"></div>
</div>

</template>

<script>
export default {
 props: { seller: { type: Object, default: { supports: [] } } },

 created() { this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'] }

}

</script>

<style scoped>
@import "../../common/style/mixin.css";

.header{
	background: rgba(7, 17, 27, 0.5);
	color:#fff;
}
.content-wrapper{
	position: relative;
	padding: 24px 12px 18px 24px;
    font-size: 0;
}
.avatar{
	display: inline-block;
	vertical-align: top;
	
}
.avatar img{
	/*width="64" height="64"*/
	width:64px;
	height: 64px;
	border-radius: 3px;
}

.content{
	display: inline-block;
	margin-left: 16px;
	font-size: 14px;
}
.title{
	margin: 2px 0 8px 0;
}
.brand{
	display: inline-block;
	vertical-align: top;
	width: 30px;
	height: 18px;
    background-image: url(../../../resource/img/brand@2x.png);
    background-size: 30px 18px;
    background-repeat: no-repeat;

}
.name{
	margin-left: 6px;
	font-size: 16px;
	line-height: 18px;
	font-weight: bold;
}
.description{
	font-size: 12px;
	color:rgb(255,255,255);
	font-weight: 200;
	line-height: 12px;
}
.supports{
	margin-top: 5px;
}
.supports .icon{
    display: inline-block;
    width: 12px;
    height: 12px;
    vertical-align: top;
    margin-right: 4px;
    background-size: 12px 12px;
    background-repeat: no-repeat;    
}
.icon .decrease{
	 @include bg-image("decrease_1");
	background-image: url(../../../resource/img/decrease_1@2x.png);
}
.icon .discount{
	 @include bg-image("discount_1");
	background-image: url(../../../resource/img/discount_1@2x.png);
}
.icon .guarantee {
     @include bg-image("guarantee_1");
    background-image: url(../../../resource/img/guarantee_1@2x.png);
}
.icon .invoice {
     @include bg-image("invoice_1");
    background-image: url(../../../resource/img/invoice_1@2x.png);
}
.icon .special {
     @include bg-image("special_1");
    background-image: url(../../../resource/img/special_1@2x.png);
}
.supports .text{
	font-size: 10px;
	line-height: 12px;
}
.supports-count{
	position: absolute;
	right: 12px;
	bottom: 18px;
	padding: 0 8px;
	height: 24px;
	line-height: 24px;
	border-radius: 14px;
	background:rgba(0,0,0, 0.2);
	text-align: center;
}
.count{
	font-size: 10px;
	vertical-align: top;
}
.icon-arrow_right{
	   margin-left: 2px;
       line-height: 24px;
       font-size: 10px;
}

</style>
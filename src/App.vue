<template>
<div>
  <div v-if="blacksrc==1" class="black_scr">
    <div class="white_scr">
      <h4>상세페이지임</h4>
      <p>상세 페이지 내용임</p>
      <span class="close" @click="close">닫기</span>
    </div>
  </div>
<div class="menu">
  <a v-for="(i) in menus" :key="i">{{i}}</a>
</div>
  <span class="product">
    <div v-for="(key,index) in datas" :key="index" class="room_box">
    <img :src="key['image']" class="room-img">
    <h4 @click="model_Open">{{key.content}}</h4>
    <p>{{key.price.toLocaleString()}}원</p>
    <button @click="btn(index)">허위매물신고버튼</button>
    <span>신고수 : {{call[index]}}</span>
    </div>
  </span>
  </div>

</template>

<script>
import array from "./assets/room.js";
console.log(array)
export default {
  name: 'AppleVueApp',

  data() {
    return {
      datas:array,
      blacksrc:0,



      // srcimg:[require("./assets/room0.jpg"),require('./assets/room1.jpg'),require('./assets/room2.jpg')],
      call:[0,0,0,0,0,0],
      // price:[60,70,120],
      // products:['역삼동원룸','천호동원룸','마포구원룸'],
      // menus:['home','product','about']
    };
  },


  mounted() {
    
  },

  methods: {
    btn:function(index){
      console.log(index)
      this.call[index]++
    },
    model_Open:function(){
      this.blacksrc=true
    },
    close:function(){
      this.blacksrc=false
    },

  },

};
</script>

<style>
body{
  margin: 0;
  padding: 0;
}
.menu{
  width: 100%; height: 50px;
  display: flex;
  flex-wrap: nowrap;
  flex-direction: row;
  align-items: center;
  background-color: darkblue;
  border-radius: 5px;
}
.menu a{
  width: 33.3%;
  height: 100%;
  text-align: center;
  color: white;
  line-height: 50px;
  cursor: pointer;
}
.product{
  display: block;
  width: 100%;
  height: auto;
  display: flex;
  flex-flow: column wrap;
  justify-content: center;
  align-items: center;
  
}
.room_box{
  width: 100%;
  height: 400px;
  display: flex;
  flex-flow: column wrap;
  justify-content: center;
  align-items: center;
}
.room-img{
  width: 100%;
  height: 200px;
  object-fit: contain;
}
.black_scr{
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed; 
  padding: 20px;
  box-sizing: border-box;
}
.white_scr{
  width: 100%;
  border-radius: 10px;
  background-color: white;
  padding: 20px;
  box-sizing: border-box;
  text-align: center;
}
.close{
  width: 120px;
  height: 35px;
  line-height: 35px;
  text-align: center;
  background-color: black;
  color: white;
  cursor: pointer;
  display: block;
  margin: 0 auto;
}
</style>
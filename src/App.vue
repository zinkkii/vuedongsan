<template>
  
  <!--Modal-->
  <!-- <div class="start" :class="{end : modal_status}"> -->
  <transition name="fade">
    <Modal @closeModal="modal_status=false" 
    v-if="modal_status == true" :data="data"
     :modal_click="modal_click" />
  </transition>
  <!-- </div> -->

  <!--Nav-->
  <div class="menu">
    <a v-for="(menu,i) in menus" :key="i">{{ menu }}</a>
  </div>

  <!--Discount Event-->
  <Discount />

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>
  
  <!--Contents-->
  <Card @openModal="modal_status=true; modal_click= i" v-for="(data,i) in data" :key="i" :data="data" />

</template>

<script>

import data from './assets/roomdata.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data() {
    return { 
      data_ori: [...data], //data사본
      data: data,
      menus: ['Home','Products','About'],
      modal_status: false,
      modal_click: 0,
    }
  },
  methods: {
    count_up(){
      this.data.block_count++;
    },
    priceSort() {
      this.data.sort(function(a,b){
        return a.price-b.price;
      })
    },
    sortBack() {
      this.data = [...this.data_ori];
    }
  },
  beforeMount() { //마운트되기전 뭘 하고싶으면 여기에

  }
  ,
  mounted() { //마운트되고난후 뭘 하고싶으면 여기에
    // setTimeout(() => {
    //   this.show_discount = false;
    // },2000);
  },
  created() {
    //HTML 작성후, ~~
  },
  components: {
    Discount: Discount,
    Card: Card,
    Modal: Modal
}
}
</script>

<style>
.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.7s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 0.7s;
}
.fade-leave-to {
  opacity: 0;
}

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 25px;
}
.white-bg {
  width:100%; background: white;
  border-radius: 5px; padding: 25px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 5px;
}
.menu {
  background: darkslateblue;
  color: #fff;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  padding : 10px;
}
.room-img {
  width:100%;
  max-height: 300px;
  margin-top: 40px;
}
</style>

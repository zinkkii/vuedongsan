<template>
  <!--Modal-->
  <div class="black-bg">
    <div class="white-bg">
      <img :src="data[modal_click].image" class="room-img">
      <h2>{{data[modal_click].title}}</h2>
      <p>{{data[modal_click].content}}</p>
			<input v-model="month" placeholder="개월수 입력">
			<input type="range" min="1" max="24" v-model="month">
      <p>{{month}}개월 선택됨 : <b>{{data[modal_click].price * month}} ₩ </b></p>
      <p @click="$emit('closeModal')"><b>[Close]</b></p>
    </div>
  </div>
</template>

<script>
export default {
	name: 'Modal-event',
	props: {
		data: Array,
		modal_click: Number
	},
	data() {
		return {
			month : 1,
		}
	},
	watch : {
		month(a) { // 위의 데이터랑 이름 맞춰야됨 month데이터가 변할때마다 여깄는코드 실행됨
			//a(앞에있는 변수=변경된데이터), b(뒤에있는변수=변경전데이터)
			if(a > 24) {
				alert('최대 24개월까지 가능');
				this.month=1;
			}
			if(isNaN(a) == true) {
				alert('문자 입력하지 마세요. 숫자만 입력하세요');
				this.month=1;
			}
			// if(a==2) {
			// 	alert('2개월은 안합니다.');
			// 	this.month=1;
			// }
		}
	},
	beforeUpdate() {
		if(this.month==2) {
			alert('2개월은 안팔아요');
			this.month=1;
		}
	}
}
</script>

<style>

</style>
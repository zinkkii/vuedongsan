<template>

<div class="event">
    <h3>지금 결제하면 {{discountdown}}% 할인해드림</h3>
</div>

</template>

<script>
export default {
  name: 'Discount-event',
  methods: {
    setInterval
  },
  data() {
    return {
      discountdown: 30,
    }
  },
  mounted() {
    setInterval(() => {
      if(this.discountdown > 0){
        this.discountdown--;
      }
    },1000);
  },
}
</script>

<style>
.event {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
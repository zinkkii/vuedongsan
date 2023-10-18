<template>
  <!--Contents-->
  <div>
    <div>
      <img :src=data.image class="room-img">
      <h3 @click="$emit('openModal', data.id)">{{data.title}}</h3>
      <p>{{data.price}} ₩</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card-event',
  props: {
      data: Object,
  }
}
</script>

<style>

</style>
<template>
  <div>
    <img :src="room.image" class="room-img">
    <h4 @click="modalOpenFunc"> {{ room.title }} </h4>
    <p> {{ room.price }} 원</p>
  </div>
</template>

<script>
export default {
    name : 'CardApp',
    props : {
        room : Object,
    },
    methods : {
        modalOpenFunc() {
            this.$emit('openModal', this.room.id);
        }
    },
}
</script>

<style>

</style>
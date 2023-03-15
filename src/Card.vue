<template>
      <div>
    <img :src="oneroom.image" class="room-img" />
    <h4 @click="send">
      {{ oneroom.title }}
    </h4>
    <p>{{ oneroom.price }}원</p>
  </div>
</template>

<script>
export default({
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Card',
    props: {
        oneroom: Object,
    },
    methods: {
        send() {
            this.$emit('openModal', this.oneroom.id)
        }
    },
})
</script>

<style scoped>
.room-img {
  width:50%;
  margin-top: 40px;
}
</style>

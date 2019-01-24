<template lang="pug">
  div
    transition(name="fade")
      .modal(v-if="visible" :class="visiblility")
        .modal-background
        .modal-content.box
          p Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium at atque consectetur dolorem doloribus, libero minus molestiae mollitia neque nulla quasi similique sunt veritatis, voluptates voluptatum! Dolores nesciunt sed voluptas?
        button.modal-close.is-large(@click.prevent='close')

</template>

<script>
export default {
  name: 'modal',
  props: ['visible', 'visiblility'],
  data() {
    return {

    };
  },
  methods: {
    close() {
      this.visible = false;
      this.visiblility = '';
    },
    open() {
      console.log('clicked');
      this.visible = true;
      this.visiblility = 'is-active';
    },
  },
};
</script>

<style scoped>
  .fade-enter-active, .fade-leave-active{
    transition: all 0.5s ease-in-out;
    transform: scale(1);
  }
  .fade-enter, .fade-leave-active{
    opacity: 0;
    transform: scale(0.3);
  }
</style>

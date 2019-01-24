<template lang="pug">
  div
    button.button.is-primary(@click="toggle") toggle
    transition(name="fade", mode="out-in")
      article.message(:class="type", v-if="visible", key="visible" )
        .message-header
          p Primary
          button.delete(aria-label='delete', @click="close()")
        .message-body
          |{{message}}
      article.message(class="is-info", v-else, key="!visible")
        .message-header
          p Primary
          button.delete(aria-label='delete', @click="close()")
        .message-body
          |{{message}}
</template>

<script>

export default {
  name: 'alert',
  data() {
    return {
      message: 'salut',
      type: 'is-primary',
      visible: true,
    };
  },
  methods: {
    toggle() {
      this.visible = !this.visible;
    },
    close() {
      this.visible = !this.visible;
    },
  },
};
</script>

<style scoped>
.fade-enter-active, .fade-leave-active{
  transition: all 0.75s ease;
  transform:  translateX(0);
}
.fade-enter, .fade-leave-active{
  opacity: 0;
  transform:  translateX(150px);
}
</style>

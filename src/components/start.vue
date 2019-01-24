<template lang="pug">
section.section
  .container
    a.button.is-primary(@click="addPersons") ajouter une personne
    .field
      .control
        input.input.is-primary(type='text', placeholder='Primary input', v-model="message")
    article.message.is-info(:class="{ 'is-warning': success, 'is-danger': !success }")
      .message-header
        p Danger
      .message-body
        |{{personnes}}
    alert

</template>
<script>
import alert from './alert.vue';

export default {
  name: 'start',
  components: { alert },
  data() {
    return {
      message: 'salut',
      success: false,
      personnes: ['Ouali', 'Hachehouche', 'Mokrane'],
      messgae: '',
    };
  },
  props: {
    msg: String,
  },
  methods: {
    addPersons() {
      if (this.message === '') {
        console.log('le champ est vide');
      } else {
        this.personnes.push(this.message);
        this.message = '';
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="sass">

.container
  max-width: 1200px
  margin: 0 auto
</style>

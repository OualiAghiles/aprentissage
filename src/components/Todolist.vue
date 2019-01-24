<template lang="pug">
section.section
  .columns
    .is-12.column
      h1.title.is-1 Todolist
  .columns
    .is-4.column.is-offset-4
      nav.panel.has-background-white
        p.panel-heading
          | repositories
        .panel-block
          .field.has-addons
            .control
              input.input(type='text', placeholder='Ajouter une tâche' v-model="newTodo", @keyup.enter="addTodo")
            .control
              a.button.is-info(@click.prevent="addTodo")
                | +
        p.panel-tabs
          a.is-active all
          a public
          a private
        a.panel-block(v-for='todo in filtredTodos', :class="{'completed': todo.completed}")
          span.panel-icon
            label.checkbox
              input(type='checkbox', v-model="todo.completed" )
          span.text
            | {{todo.name}}
        .panel-block
          nav.breadcrumb.is-small(aria-label='breadcrumbs', style="margin: auto;")
            ul
              li
                a(href='#' @click.prevent="filter = 'all'")
                  span.icon.is-small
                    i.fas.fa-home(aria-hidden='true')
                  span  All ( {{allTodos}} )
              li
                a(href='#' @click.prevent="filter = 'remaining'")
                  span.icon.is-small
                    i.fas.fa-list(aria-hidden='true')
                  span remaining
                  span.strong ( {{remaining}} )
              li
                a(href='#' @click.prevent="filter = 'done'")
                  span.icon.is-small
                    i.fas.fa-check(aria-hidden='true')
                  span completed
                  span.strong ( {{ doneTodo }} )
              li
                a(href='#', @click.prevent="removeCompleted")
                  span.icon.is-small
                    i.fas.fa-trash(aria-hidden='true')
                  span clear


</template>

<script>

export default {
  name: 'Todolist',
  components: {},
  data() {
    return {
      todos: [{
        name: 'Tâche teste',
        completed: false,
      }],
      newTodo: '',
      filter: 'all',
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        name: this.newTodo,
        completed: false,
      });
      this.newTodo = '';
    },
  },
  computed: {
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    },
    allTodos() {
      return this.todos.length;
    },
    doneTodo() {
      return this.todos.filter(todo => todo.completed).length;
    },
    filtredTodos() {
      if (this.filter === 'remaining') {
        return this.todos.filter(todo => !todo.completed);
      }
      if (this.filter === 'done') {
        return this.todos.filter(todo => todo.completed);
      } else {
        return this.todos;
      }
    },
    removeCompleted() {
      return console.log('cleared');
    },
  },
};
</script>

<style scoped lang="sass">
.completed
  .text
    text-decoration: line-through
    color: lightgrey
  background-color: whitesmoke
</style>

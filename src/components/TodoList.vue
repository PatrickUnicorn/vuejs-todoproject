<script setup>
import { ref, reactive } from 'vue';
import TodoItem from './TodoItem.vue';
const todos = reactive([
  {
    title: 'pommes',
    done: true,
    id: 1,
  },
  {
    title: 'carotte',
    done: false,
    id: 2,
  },
  {
    title: 'poires',
    done: true,
    id: 3,
  },
]);
const debug = ref(false)
 
const newTodo = reactive({
  title: '',
  done: false,
  id: null,
});

let maxId = 4;

const addNewTodo = (event) => {
  maxId++;
  todos.push({ ...newTodo, id: maxId });
};
const handleDeleteItem = (id) => {
  const index = todos.findIndex((todo) => todo.id === id);
  todos.splice(index, 1);
};
</script>

<template>
  <pre v-if="debug">{{ todos }}</pre>
  <form class="todo-form">
    <div class="input-field">
      <input
        v-model="newTodo.title"
        type="text"
        id="input--add"
        class="input"
        placeholder="Que voulez-vous faire ?"
      />
      <label for="input--add"></label>
    </div>
    <input
      type="submit"
      class="button button--add"
      value="Ajouter"
      @click.prevent="addNewTodo"
    />
  </form>
  <ul class="todo-collection">
    <li v-for="todoItem in todos" class="todo-collection__item">
      <TodoItem
        :todo="todoItem"
        @deleteItem="handleDeleteItem"
        @click="handleDeleteItem"
      ></TodoItem>
    </li>
  </ul>
</template>

<style scoped></style>

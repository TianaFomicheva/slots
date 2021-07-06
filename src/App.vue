<template>
<div>


<!-- <List :items="users" :fields="['username','name']" :itemComponent="$options.listItemComponent.User" > -->
<List :items="users" :fields="['username','name']"  >
  <template #item="{ item:user }">
    {{ user.name }} 

  </template>

</List>

<!-- <List :items="todos" :fields="['title']" :itemComponent="$options.listItemComponent.Todo" /> -->


<!-- <List :items="todos" :fields="['title']" :itemComponent="$options.listItemComponent.Todo" > -->
<List :items="todos" :fields="['title']" >
  <template #item="slotProps">
    <Todo :item="slotProps.item" />
  </template>
</List>
 
  </div>
</template>

<script>
import List from "./components/List.vue";
// import User from "./components/User.vue";
import Todo from "./components/Todo.vue";

import { loadUsers, loadTodos } from "./api.js";
export default {
  name: "App",
  components: {
    List, Todo
  },
  data() {
    return { filter:"",
    users: [], todos:[],
  }
  },
  // listItemComponent:{
  //   User
  //   // , Todo
  // },


  mounted() {
    loadUsers().then((users) => {
      this.users = users;
    });
    loadTodos().then((todos) => {
      this.todos = todos;
    });
  },
  computed: {
    filteredUsers() {
      return this.filter
        ? this.users.filter((u) =>
            this.fields.some((f) =>
              u[f].toLowerCase().includes(this.filter.toLowerCase())
            )
          )
        : this.users;
    },
  },
};
</script>


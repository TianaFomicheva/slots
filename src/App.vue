<template>
<div>
  <!--
  <List :items="users" :fields="['username', 'name']">
    <template #item="{ item: user }">
      {{ hello }} {{ user.name }} ({{ user.username }})
    </template>
  </List>
  <hr />
  <List :items="todos" :fields="['title']">
    <template #item="slotProps">
      <Todo :item="slotProps.item" />
    </template>
  </List>
  -->

<Userlist :items="users" :fields="['username','name']"/>
 
  </div>
</template>

<script>
import Userlist from "./components/Userlist.vue";
// import List from "./components/List.vue";
// import User from "./components/User.vue";
// import Todo from "./components/Todo.vue";

import { loadUsers, loadTodos } from "./api.js";
export default {
  name: "App",
  components: {
    Userlist,
    // List,
    // Todo,
    // User
  },
  data() {
    return { filter:"",
    users: []
    };
  },


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


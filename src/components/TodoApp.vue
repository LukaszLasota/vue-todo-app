<template>
  <div class="item">
    <h2>Nowe todo: {{ newItem }}</h2>
    <input type="text" placeholder="todo" v-model="newItem" />
    <button @click="addItem">Dodaj</button>
  </div>
  <TodoItem
    v-bind:item="item"
    v-for="item in items"
    v-bind:key="item.id"
    @removeClicked="removeItem"
  />
</template>

<script>
import TodoItem from "./todoItem";
export default {
  name: "Aplikacja To Do List",
  components: {
    TodoItem,
  },
  data: function () {
    return {
      title: "Aplikacja To Do List",
      newItem: "",
      items: [
        { title: "Zrobić zakupy", completed: false, id: 1 },
        { title: "Poszprzątać ", completed: true, id: 2 },
      ],
    };
  },
  methods: {
    addItem() {
      this.items.push({
        title: this.newItem,
        completed: false,
        id: Math.random(),
      });
      this.newItem = "";
    },
    removeItem(id) {
      const index = this.items.findIndex((el) => el.id === id);
      this.items[index].completed = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.item {
  border: 1px solid grey;
  margin: 8px auto;
  padding: 10px;
  width: 40%;
}
.completed {
  opacity: 0.5;
}
.completed h2 {
  text-decoration: line-through;
}
</style>

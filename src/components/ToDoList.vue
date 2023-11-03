<template>
  <div class="container">
    <h1>To-Do List</h1>
    <div class="form-div">
      <input type="text" v-model="newItem" />
      <button @click="addNewItem">Add</button>
    </div>
    <ul class="itemsList">
      <li v-for="(toDoItem, index) in toDoItems" :key="index">
        {{ toDoItem }}<span>✅</span><span>❌</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
      toDoItems: [],
    };
  },
  methods: {
    addNewItem() {
      if (this.newItem.trim() !== "") {
        this.toDoItems.push(this.newItem);
        this.newItem = "";
      }
    },
  },
};
</script>

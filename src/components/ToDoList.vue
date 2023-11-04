<template>
  <div class="container">
    <h1>To-Do List</h1>
    <div class="form-div">
      <span>Time:</span>
      <input type="number" v-model="time" />
      <select v-model="ampm">
        <option value="AM">AM</option>
        <option value="PM">PM</option>
      </select>
      <span>To-Do:</span>
      <input type="text" v-model="newItem" />
      <button @click="addNewItem">Add</button>
    </div>
    <ul class="itemsList">
      <li v-for="(toDoItem, index) in toDoItems" :key="index">
        {{ toDoItem[0] }} {{ toDoItem[1] }} : {{ toDoItem[2] }}<span>✅</span
        ><a @click="deleteItem(index)" title="Cancel Item">❌</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      time: "",
      ampm: "AM",
      newItem: "",
      toDoItems: [],
    };
  },
  methods: {
    addNewItem() {
      if (this.newItem.trim() !== "" && this.ampm && this.time) {
        this.toDoItems.push([this.time, this.ampm, this.newItem]);
        this.time = this.newItem = "";
        this.ampm = "AM";
        this.$emit("items-updated", this.toDoItems);
      }
    },
    deleteItem(index) {
      delete this.toDoItems.splice(index, 1);
      this.$emit("items-updated", this.toDoItems);
    },
  },
};
</script>

<template>
  <div>
    <h1>To-Do List</h1>
    <div class="form-div">
      <span>Time:</span><br />
      <input type="number" v-model="time" min="0" max="12" />
      <select v-model="ampm">
        <option value="AM">AM</option>
        <option value="PM">PM</option>
      </select>
      <br />
      <span>To-Do:</span><br />
      <input type="text" v-model="newItem" />
      <button @click="addNewItem">Add</button>
    </div>
    <ul class="itemsList">
      <li v-for="(toDoItem, index) in toDoItems" :key="index" class="listItems">
        <a v-if="toDoItem.displayButton" @click="itemDone(index)">✅</a
        ><a @click="deleteItem(index)" title="Cancel Item">❌</a
        ><span class="toDoElement" :style="toDoItem.textStyle">
          {{ toDoItem.time }} {{ toDoItem.ampm }} {{ toDoItem.text }}</span
        >
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
      if (this.time > 12) {
        alert("Please add a number between 1 and 12");
      }
      if (this.newItem.trim() !== "" && this.time <= 12) {
        this.toDoItems.push({
          time: this.time,
          ampm: this.ampm,
          text: this.newItem,
          textStyle: { textDecoration: "none" }, // Initialize textStyle
          displayButton: true, // Initialize displayButton
        });
        this.time = this.newItem = "";
        this.ampm = "AM";
        this.$emit("items-updated", this.toDoItems);
      }
    },
    itemDone(index) {
      this.toDoItems[index].textStyle.textDecoration = "line-through";
      this.toDoItems[index].displayButton = false;
    },
    deleteItem(index) {
      delete this.toDoItems.splice(index, 1);
      this.$emit("items-updated", this.toDoItems);
    },
  },
};
</script>

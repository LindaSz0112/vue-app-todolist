<template>
  <div class="container">
    <ToDoList @items-updated="itemsUpdated"></ToDoList>
    <OrderingArrows
      v-if="showArrows"
      :toDoItems="toDoItems"
      @items-updated="itemsUpdated"
    ></OrderingArrows>
  </div>
</template>

<script>
import ToDoList from "@/components/ToDoList.vue";
import OrderingArrows from "@/components/OrderingArrows.vue";
import "./assets/styles.css";

export default {
  components: {
    ToDoList,
    OrderingArrows,
  },
  data() {
    return {
      showArrows: false,
      toDoItems: [],
    };
  },
  methods: {
    toggleArrows() {
      this.showArrows = this.toDoItems.length >= 2;
    },
    itemsUpdated(items) {
      this.toDoItems = items;
      this.toggleArrows();
    },
  },
};
</script>

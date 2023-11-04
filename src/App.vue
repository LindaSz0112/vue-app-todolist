<template>
  <ToDoList></ToDoList>
  <OrderingArrows
    v-if="showArrows"
    :toggle="toggleArrows"
    :toDoItems="toDoItems"
  ></OrderingArrows>
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
      if (this.toDoItems.length >= 2) {
        this.showArrows = true;
      }
    },
  },
};
</script>

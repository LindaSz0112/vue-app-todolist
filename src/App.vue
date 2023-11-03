<template>
  <ToDoList></ToDoList>
  <OrderingArrows></OrderingArrows>
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
};
</script>

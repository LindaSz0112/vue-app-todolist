<template>
  <div>
    <p>
      <a @click="orderItems('ascendingOrder')">⬆️</a>
      <a @click="orderItems('descendingOrder')">⬇️</a>
    </p>
  </div>
</template>

<script>
export default {
  props: ["toDoItems"],
  data() {
    return {
      orders: "",
    };
  },
  methods: {
    orderItems(orderType) {
      this.orders = orderType;
      // const sortedItems = [...this.toDoItems];
      if (this.orders === "ascendingOrder") {
        console.log(this.toDoItems.slice().sort((a, b) => a - b));
      }
    },
  },
};
</script>

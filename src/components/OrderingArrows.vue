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

      // Create a copy of the toDoItems prop
      const copiedToDoItems = this.toDoItems.slice();

      if (this.orders === "ascendingOrder") {
        copiedToDoItems.sort((a, b) => {
          const ampmComparison = a.ampm.localeCompare(b.ampm);

          if (ampmComparison === 0) {
            return a.time - b.time;
          }
          console.log(ampmComparison);
          return ampmComparison;
        });
      } else if (this.orders === "descendingOrder") {
        copiedToDoItems.sort((a, b) => {
          const ampmComparison = b.ampm.localeCompare(a.ampm);

          if (ampmComparison === 0) {
            return b.time - a.time;
          }
          console.log(ampmComparison);
          return ampmComparison;
        });
      }

      // Emit an event to send the sorted copy back to the parent component
      this.$emit("items-updated", copiedToDoItems);
    },
  },
};
</script>

<template>
  <div :style="selectedStyle">
    <span>{{ BtnText }}</span>
  </div>
</template>

<script>
export default {
  props: ["BtnText", "isSelected"],
  computed: {
    selectedStyle() {
      if (!this.isSelected) {
        return {
          color: "tomato",
        };
      }
      return {
        backgroundColor: "tomato",
        color: "white",
      };
    },
  },
};
</script>

<style scoped>
div {
  padding: 10px;
  margin-right: 30px;
  font-size: 14px;
}
div:hover {
  background-color: rgba(255, 165, 0, 0.4);
}
</style>

<template>
  <div :style="{ backgroundColor: headerColor }">
    <h1>{{ headerText }}</h1>
  </div>
</template>

<script>
export default {
  props: ["headerText", "headerColor"],
};
</script>

<style scoped>
div {
  width: 100%;
  height: 15vh;
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  color: white;
}
</style>

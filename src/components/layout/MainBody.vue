<template>
  <div>
    <slot name="TabMenu"></slot>
    <slot name="Contents"></slot>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
div {
  height: 100vh;
  margin-top: 15vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px;
}
</style>

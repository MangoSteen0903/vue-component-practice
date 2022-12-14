<template>
  <div :style="{ marginBottom: marginBottom }">
    <slot></slot>
    <section>
      <slot name="Buttons"></slot>
    </section>
  </div>
</template>

<script>
export default {
  props: ["marginBottom"],
};
</script>

<style scoped>
div {
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
  width: 90%;
  padding: 20px;
  border-radius: 15px;
  display: flex;
}
section {
  display: flex;
}
</style>

<template>
  <BaseContent
    v-for="(item, index) in items"
    :title="item.title"
    :description="item.description"
    :link="item.link"
    :key="index"
    @delete-content="deleteEvent(index)"
  />
</template>
<script>
import BaseContent from "../base/BaseContent.vue";

export default {
  components: { BaseContent },
  props: ["items"],
  emits: ["delete-item"],
  methods: {
    deleteEvent(index) {
      this.$emit("delete-item", index);
    },
  },
};
</script>

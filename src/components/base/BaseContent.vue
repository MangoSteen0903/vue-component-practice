<template>
  <BaseBox margin-bottom="30px">
    <template #default>
      <section id="header">
        <h1>{{ title }}</h1>
        <BaseButton class="btn" BtnText="Delete" @click="deleteContent" />
      </section>
      <section id="contents">
        <span>{{ description }}</span>
        <a :href="link">
          <span id="btn"> View Resource </span>
        </a>
      </section>
    </template>
  </BaseBox>
</template>

<script>
import BaseBox from "./BaseBox.vue";
import BaseButton from "./BaseButton.vue";

export default {
  props: ["title", "description", "link"],
  components: { BaseBox, BaseButton },
  methods: {
    deleteContent() {
      this.$emit("delete-content");
    },
  },
};
</script>

<style scoped>
#header {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

#header span {
  color: tomato;
}

#contents {
  display: flex;
  flex-direction: column;
  width: 100%;
}
#contents span {
  margin-bottom: 5px;
}
#contents #btn {
  color: orange;
  font-weight: 600;
}
.btn {
  margin: 0;
}
</style>

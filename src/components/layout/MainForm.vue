<template>
  <BaseBox>
    <template #default>
      <form @submit.prevent>
        <div>
          <label>Title</label>
          <input type="text" v-model="inputTitle" />
        </div>

        <div>
          <label>Description</label>
          <textarea type="text" v-model="inputDescription" id="description" />
        </div>
        <div>
          <label>Link</label>
          <input type="text" v-model="inputLink" />
        </div>

        <BaseButton
          BtnText="Add Resources"
          isSelected="true"
          class="btn"
          @click="onClick"
        />
      </form>
    </template>
  </BaseBox>
</template>

<script>
import BaseBox from "../base/BaseBox.vue";
import BaseButton from "../base/BaseButton.vue";

export default {
  components: { BaseBox, BaseButton },
  data() {
    return {
      inputTitle: "",
      inputDescription: "",
      inputLink: "",
    };
  },
  methods: {
    onClick() {
      let msg = "";
      switch (true) {
        case this.inputTitle.trim() === "":
          msg = "You should write title to submit this form.";
          this.$emit("input-error", msg);
          break;
        case this.inputDescription.trim() === "":
          msg = "You should write description to submit this form.";
          this.$emit("input-error", msg);
          break;
        case this.inputLink.trim() === "":
          msg = "You should write link to submit this form.";
          this.$emit("input-error", msg);
          break;
        default:
          this.$emit(
            "enter-value",
            this.inputTitle,
            this.inputDescription,
            this.inputLink
          );
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
div {
  display: flex;
  flex-direction: column;
  margin-bottom: 30px;
}
div label {
  margin-bottom: 10px;
  font-weight: 600;
}

#description {
  height: 100px;
}

div:nth-child(3) {
  margin-bottom: 40px;
}

.btn {
  width: 130px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

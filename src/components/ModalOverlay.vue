<template>
  <teleport to="body">
    <div class="modal-mask" @click="cancelModal">
      <BaseBox class="modal">
        <h1 class="title">{{ title }}</h1>
        <span>{{ errMsg }}</span>
        <div>
          <BaseButton
            @click="closeModal"
            :BtnText="btnName"
            isSelected="true"
            class="btn"
          />
        </div>
      </BaseBox>
    </div>
  </teleport>
</template>

<script>
import BaseBox from "./base/BaseBox.vue";
import BaseButton from "./base/BaseButton.vue";

export default {
  emits: ["close-modal", "cancel-modal"],
  props: ["errMsg", "title", "btnName"],
  components: { BaseBox, BaseButton },
  methods: {
    closeModal() {
      this.$emit("close-modal");
    },
    cancelModal() {
      this.$emit("cancel-modal");
    },
  },
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal {
  width: 60%;
  height: 25%;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}
.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 60px;
  height: 30px;
  margin: 0;
}
div {
  display: flex;
  justify-content: flex-end;
}
</style>

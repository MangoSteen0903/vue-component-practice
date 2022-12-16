<template>
  <BaseBox marginBottom="50px">
    <template #Buttons>
      <BaseButton
        v-for="btn in buttonStatus"
        :BtnText="btn.text"
        :isSelected="btn.isSelect"
        :key="btn.id"
        @click="selectBtn(btn.id)"
      />
    </template>
  </BaseBox>
</template>

<script>
import BaseBox from "./base/BaseBox.vue";
import BaseButton from "./base/BaseButton.vue";
export default {
  components: { BaseBox, BaseButton },
  props: ["currentlySelected"],
  data() {
    return {
      buttons: ["Stored Resources", "Add Resource"],
      buttonStatus: [],
    };
  },
  watch: {
    currentlySelected() {
      this.buttonStatus.map((element, index) => {
        if (index === this.currentlySelected) {
          element.isSelect = true;
        } else {
          element.isSelect = false;
        }
      });
    },
  },
  methods: {
    selectBtn(id) {
      this.buttonStatus.map((element, index) => {
        if (index === id) {
          element.isSelect = true;
        } else {
          element.isSelect = false;
        }
      });
      this.$emit("selectTab", id);
    },
  },
  mounted() {
    this.buttons.map((text, id) => {
      const newBtnStatus = {
        id,
        text,
        isSelect: id === 0 ? true : false,
      };
      this.buttonStatus.push(newBtnStatus);
    });
  },
};
</script>

<style scoped></style>

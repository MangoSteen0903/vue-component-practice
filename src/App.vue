<template>
  <ModalOverlay
    @close-modal="closeModal(this.targetContent)"
    @cancel-modal="closeModal"
    v-if="isModalVisible"
    :title="modalTitle"
    :btnName="modalBtnName"
    :errMsg="errMsg"
  />
  <TopHeader headerText="Learning Resources App" headerColor="tomato" />
  <MainBody>
    <template #TabMenu>
      <TabMenu @selectTab="changeTab" :currentlySelected="currentId" />
    </template>
    <template #Contents>
      <component
        :is="currentTab"
        v-bind="{ items }"
        @delete-item="confirmModal"
        v-if="currentTab === 'MainContent'"
      />
      <KeepAlive>
        <component
          :is="currentTab"
          @enter-value="submitValue"
          @input-error="appearFormErrorModal"
          v-if="currentTab === 'MainForm'"
        />
      </KeepAlive>
    </template>
  </MainBody>
</template>

<script>
import MainBody from "./components/layout/MainBody.vue";
import MainContent from "./components/layout/MainContent.vue";
import TabMenu from "./components/TabMenu.vue";
import TopHeader from "./components/TopHeader.vue";
import MainForm from "./components/layout/MainForm.vue";
import BaseContent from "./components/base/BaseContent.vue";
import ModalOverlay from "./components/ModalOverlay.vue";
export default {
  name: "App",
  components: {
    TopHeader,
    TabMenu,
    MainBody,
    MainContent,
    MainForm,
    BaseContent,
    ModalOverlay,
  },
  computed: {
    currentTab() {
      return this.tabList[this.currentId];
    },
  },
  data() {
    return {
      tabList: ["MainContent", "MainForm"],
      currentId: 0,
      items: [],
      isModalVisible: false,
      errMsg: "",
      modalTitle: "",
      modalBtnName: "",
      isTabInverted: false,
      targetContent: undefined,
    };
  },
  methods: {
    changeTab(id) {
      this.currentId = id;
    },
    submitValue(title, description, link) {
      const newItem = {
        title,
        description,
        link,
      };
      this.items.push(newItem);
      this.currentId = 0;
      this.isTabInverted = true;
    },
    appearFormErrorModal(msg) {
      this.errMsg = msg;
      this.modalTitle = "Invalid Input";
      this.modalBtnName = "Dismiss";
      this.isModalVisible = !this.isModalVisible;
    },
    appearDeleteModal() {
      this.errMsg = "This will cause a data loss. Are you sure?";
      this.modalTitle = "Delete Content";
      this.modalBtnName = "Yes.";
      this.isModalVisible = !this.isModalVisible;
    },
    closeModal(id) {
      this.isModalVisible = !this.isModalVisible;
      if (typeof this.targetContent !== "undefined") {
        this.items = this.items.filter((element, index) => id !== index);
      }
      this.targetContent = undefined;
    },
    confirmModal(id) {
      this.appearDeleteModal();
      this.targetContent = id;
    },
  },
};
</script>

<style>
/*
  1. Use a more-intuitive box-sizing model.
*/
*,
*::before,
*::after {
  box-sizing: border-box;
}
/*
  2. Remove default margin
*/
* {
  margin: 0;
}
/*
  3. Allow percentage-based heights in the application
*/
html,
body {
  height: 100%;
}
/*
  Typographic tweaks!
  4. Add accessible line-height
  5. Improve text rendering
*/
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}
/*
  6. Improve media defaults
*/
img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}
/*
  7. Remove built-in form typography styles
*/
input,
button,
textarea,
select {
  font: inherit;
}
/*
  8. Avoid text overflows
*/
p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
}

a {
  color: #fff;
  text-decoration: none;
  outline: none;
}

a:hover,
a:active {
  text-decoration: none;
  color: #fff;
}
</style>

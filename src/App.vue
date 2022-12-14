<template>
  <TopHeader headerText="Learning Resources App" headerColor="tomato" />
  <MainBody>
    <template #TabMenu>
      <TabMenu />
    </template>
    <template #Contents>
      <MainContent />
    </template>
  </MainBody>
</template>

<script>
import MainBody from "./components/layout/MainBody.vue";
import MainContent from "./components/MainContent.vue";
import TabMenu from "./components/TabMenu.vue";
import TopHeader from "./components/TopHeader.vue";

export default {
  name: "App",
  components: { TopHeader, TabMenu, MainBody, MainContent },
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
</style>

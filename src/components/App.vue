<template>
  <div class="container">
    <Switch />
    <Header :headerChange="headerChange" />
    <SearchBox @on-change-event="updateHeaderStatus" />
    <ResultsContainer :suggestedName="suggestedNames" />
    <Footer />
  </div>
</template>

<script>
import { ref } from "vue";
import name from "@rstacruz/startup-name-generator";

import Header from "./Header.vue";
import SearchBox from "./SearchBox.vue";
import ResultsContainer from "./ResultsContainer.vue";
import Footer from "./Footer.vue";
import Switch from "./Switch.vue";

export default {
  components: {
    Header,
    Footer,
    SearchBox,
    ResultsContainer,
    Switch,
  },

  setup() {
    const headerChange = ref(true);
    const keyword = ref("");
    const suggestedNames = ref([]);

    const updateHeaderStatus = (key) => {
      headerChange.value = !headerChange.value;
      keyword.value = key;
      suggestedNames.value = keyword.value ? name(keyword.value) : [];
    };

    return { headerChange, keyword, suggestedNames, updateHeaderStatus };
  },
};
</script>

<style>
@import "../assets/colors.css";

body {
  margin: 0;
  padding: 0;
  background: var(--bg-color);
  overflow-x: hidden;
  color: var(--font-color);
  font-family: "Lato", sans-serif;
  transition: all 1s;
}

.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>

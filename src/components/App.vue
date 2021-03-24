<template>
  <Header :headerChange="headerChange" />
  <SearchBox @on-change-event="updateHeaderStatus" />
  <Footer />
</template>

<script>
import Header from "./Header.vue";
import SearchBox from "./SearchBox.vue";
import ResultsContainer from "./ResultsContainer.vue";
import Footer from "./Footer.vue";

export default {
  components: {
    Header,
    Footer,
    SearchBox,
  },
  data() {
    return {
      headerChange: true,
      keyword: "",
      suggestedNames: [],
    };
  },
  methods: {
    updateHeaderStatus(keyword) {
      this.headerChange = !this.headerChange;
      this.keyword = keyword;
      this.suggestedNames = keyword ? setName : [];
    },
  },
  computed: {
    setName() {
      return name(this.keyword);
    },
  },
};
</script>

<style></style>

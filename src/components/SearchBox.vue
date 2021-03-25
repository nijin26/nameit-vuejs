<template>
  <div class="search-container">
    <input
      v-model="keywordInput"
      @input="onChange()"
      type="text"
      placeholder="Type Keyword"
      class="search-input"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      keywordInput: "",
    };
  },
  methods: {
    onChange() {
      this.$emit("on-change-event", this.keywordInput);
    },
  },
};
</script>

<style>
.search-container {
  display: flex;
  justify-content: center;
  margin: 10px;
}

.search-input {
  padding: 8px 15px;
  font-size: 15px;
  width: 250px;
  border-width: 0;
  background-color: var(--primary-color);
  color: var(--font-color);
  border-radius: 50px;
  box-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
}

.search-input::placeholder {
  color: var(--font-color);
}

.search-input:focus {
  outline: none;
}
</style>

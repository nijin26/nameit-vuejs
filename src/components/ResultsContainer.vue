<template>
  <div class="results-container">
    <a
      v-for="name of Names"
      :key="name"
      target="_blank"
      class="link"
      :href="url(name)"
    >
      <div class="namecard">
        <p class="name">{{ name }}</p>
      </div>
    </a>
  </div>
</template>

<script>
export default {
  props: {
    suggestedName: {
      require: true,
      type: Array,
    },
  },
  methods: {
    url(name) {
      return `https://www.namecheap.com/domains/registration/results/?domain=%27%3B${name}`;
    },
  },
  computed: {
    Names() {
      return this.suggestedName;
    },
  },
};
</script>

<style>
.results-container {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  padding: 20px 40px;
}

.namecard {
  color: var(--font-color);
  background-color: var(--secondary-color);
  margin: 10px 15px;
  min-width: 75px;
  padding: 10px 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 5px rgba(255, 255, 255, 0.1);
  transition: background 0.35s;
  display: flex;
  justify-content: center;
}

.namecard:hover {
  background: #4a5079;
  box-shadow: 0 0 5px rgba(255, 255, 255, 0.2);
}

.name {
  margin: 0;
  font-weight: 400;
}

.link {
  text-decoration: none;
}
</style>

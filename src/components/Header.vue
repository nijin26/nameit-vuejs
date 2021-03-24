<template>
  <div class="head-container">
    <img
      src="https://user-images.githubusercontent.com/26179770/106359099-693e3380-6336-11eb-8069-9e36f25de5ca.png"
      alt="nameit"
      :class="[
        headerChange ? 'head-image-exapanded' : 'head-image-contracted',
        'head-image',
      ]"
    />
    <h1
      :class="[
        headerChange ? 'head-text-exapanded' : 'head-text-contracted',
        'head-text',
      ]"
    >
      Name It
    </h1>
  </div>
</template>

<script>
export default {
  props: {
    headerChange: {
      type: Boolean,
      require: true,
    },
  },
};
</script>

<style>
.head-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 60px;
}

.head-image {
  width: 300px;
  transition: max-width 1s, min-width 1s;
}

.head-image-exapanded {
  min-width: 220px;
  max-width: 280px;
}

.head-image-contracted {
  min-width: 100px;
  max-width: 120px;
}

.head-text {
  font-family: "Hachi Maru Pop", cursive;
  margin: 5px 0 15px 0;
  transition: font-size 1s;
}

.head-text-expanded {
  font-size: 36px;
}

.head-text-contracted {
  font-size: 12px;
}
</style>

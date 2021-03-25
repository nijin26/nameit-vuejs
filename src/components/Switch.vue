<template>
  <div class="theme-switch-wrapper">
    <label class="theme-switch" for="checkbox">
      <input type="checkbox" :checked="checked" :ref="toggleSwitch" />
      <div class="slider round" @click="checked = !checked"></div>
    </label>
  </div>
</template>

<script>
import { onMounted, onUpdated, ref } from "vue";
export default {
  setup() {
    const checked = ref(false);
    const toggleSwitch = ref(null);

    onUpdated(() => {
      if (checked.value) {
        document.documentElement.setAttribute("data-theme", "dark");
      } else {
        document.documentElement.setAttribute("data-theme", "light");
      }
    });

    return { checked, toggleSwitch };
  },
};
</script>

<style>
.theme-switch-wrapper {
  margin-top: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.theme-switch {
  display: inline-block;
  height: 34px;
  position: relative;
  width: 60px;
}

.theme-switch input {
  display: none;
}

.slider {
  background-color: #a592f2;
  bottom: 0;
  cursor: pointer;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
  transition: 0.4s;
}

.slider:before {
  background-color: #fff;
  bottom: 4px;
  content: "";
  height: 26px;
  left: 4px;
  position: absolute;
  transition: 0.4s;
  width: 26px;
}

input:checked + .slider {
  background-color: #282d4f;
}

input:checked + .slider:before {
  transform: translateX(26px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>

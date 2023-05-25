<template>
  <div>
    <button @click="change(1)">切换组件One</button>
    <button @click="change(2)">切换组件Two</button>
    <button @click="change(3)">切换组件Tree</button>
    <one-view v-if="show === 1"></one-view>
    <two-view v-if="show === 2"></two-view>
    <computer-view v-if="show === 3"></computer-view>
  </div>
</template>

<script>
import { ref } from "vue";
import OneView from "./components/OneView.vue";
import TwoView from "./components/TwoView.vue";
import ComputerView from './components/ComputerView.vue';

export default {
  name: "App",

  setup() {
    let show = ref(0);
    const change = (num) => {
      show.value = num;
    };

    return {
      show,
      change,
    };
  },

  components: {
    OneView,
    TwoView,
    ComputerView
  },
};
</script>

<style>
</style>
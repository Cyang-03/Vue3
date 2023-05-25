<template>
  <div>
    <h1>ComputerView</h1>
    <h2>{{ num }}</h2>
    <h2>{{ numNew }}</h2>
    <input type="text" v-model="inner">
  </div>
</template>

<script>
import { computed, ref } from "vue";
export default {
  setup() {
    let num = ref(60);
    let numNew = computed(() => {
        return num.value + 2
    })

    // let inner = computed(() => {
    //     return num.value + 6
    // })

    let inner = computed({
        get() {
            return num.value + 3
        },
        set(val) {
            num.value = val
        }
    })

    return {
      num,
      inner,
      numNew
    };
  },
};
</script>

<style>
</style>
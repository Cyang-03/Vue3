<template>
  <div>你好</div>
  <div>
    <h1>鼠标位置：</h1>
    <h2>X轴: {{ mouse.x }}</h2>
    <h2>y轴: {{ y }}</h2>
    <h3>{{ msg }}</h3>
    <button @click="btnMsg">修改Msg</button>
    <button @click="btnX">修改X</button>
    <button @click="btnY">修改Y</button>
    <h2>{{ name }}</h2>
    <h2>{{ age }}</h2>
  </div>
</template>

<script>
import { onMounted, reactive, ref, toRef, toRefs } from "vue";

export default {
  name: "OneView",
  setup() {
    const mouse = reactive({
      x: 0,
      y: 0,
    });
    const obj = reactive({
      name: "ybh",
      age: 18,
      gender: 'man'
    });
    const obj2 = toRefs(obj);

    const y = toRef(mouse, "y");
    // console.log(y);
    // let msg = "我是xxxx";
    let msg = ref('我是xxxx')

    const btnMsg = () => {
      msg.value = 'family who knows'
    };

    const btnX = () => {
      mouse.x++;
    };

    const btnY = () => {
      y.value++;
    };
    onMounted(() => {});

    return { mouse, msg, btnX, y, btnY, ...obj2, btnMsg };
  },
};
</script>

<style>
</style>
<template>
  <div>
    <h1>鼠标移动：</h1>
    <h2>X轴: {{ x }}</h2>
    <h2>Y轴: {{ y }}</h2>
  </div>
</template>

<script>
import { onMounted, onUnmounted, reactive, toRefs } from "vue";
const useMouse = () => {
  const mouse = reactive({
    x: 0,
    y: 0,
  });
  const moves = (e) => {
    mouse.x = e.pageX;
    mouse.y = e.pageY;
  };
  onMounted(() => {
    document.addEventListener("mousemove", moves);
  });
  onUnmounted(() => {
    document.removeEventListener("mousemove", moves);
  });
  return mouse;
};

export default {
  setup() {
    // const mouse = reactive({
    //   x: 0,
    //   y: 0,
    // });
    // const mouses = toRefs(mouse);

    const move = useMouse();

    return {
      ...toRefs(move),
    };
  },
};
</script>

<style>
</style>
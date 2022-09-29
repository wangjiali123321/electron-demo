<template>
  <div class="cropper">
    <canvas id="myCanvas" width="400" height="400"></canvas>

    <div class="rotateRight">111111</div>
  </div>
</template>

<script setup>
import { onMounted, reactive, ref } from "vue";

onMounted(async () => {
    const c = document.getElementById("myCanvas");
      const ctx = c.getContext("2d");

      ctx.fillStyle = "#999";
      ctx.fillRect(0, 0, 400, 30);
      ctx.save(); // 保存当前状态 01

      ctx.fillStyle = "#09F";
      ctx.fillRect(0, 30, 400, 30);
      ctx.save(); // 保存当前状态 02

      ctx.fillStyle = "#333";
      ctx.fillRect(0, 60, 400, 30);

      ctx.restore(); // 取出保存的状态 02 恢复
      ctx.fillRect(0, 90, 400, 30);

      ctx.restore(); // 取出保存的状态 01 恢复
      ctx.fillRect(0, 120, 400, 30);
});

</script>
<style lang="scss">
.cropper{
  .rotateRight{
    animation: changeright 1.5s linear infinite;
  }
  @keyframes changeright {
    0% {
      transform: rotate(0deg);
    }
    50% {
      transform: rotate(180deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
}
</style>

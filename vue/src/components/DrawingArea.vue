<template>
    <div>
      <canvas ref="canvas" @mousedown="startDrawing" @mousemove="draw" @mouseup="stopDrawing"></canvas>
    </div>
</template>

<script>
export default {
    data() {
      return {
        context: null,
        isDrawing: false,
      };
    },
    mounted() {
      this.context = this.$refs.canvas.getContext('2d');
    },
    methods: {
      startDrawing(event) {
        this.isDrawing = true;
        const { offsetX, offsetY } = event;
        this.context.beginPath();
        this.context.moveTo(offsetX, offsetY);
      },
      draw(event) {
        if (!this.isDrawing) return;
        const { offsetX, offsetY } = event;
        this.context.lineTo(offsetX, offsetY);
        this.context.stroke();
      },
      stopDrawing() {
        this.isDrawing = false;
      },
    },
  };
</script>

<style>
canvas {
    border: 1px solid #000;
}
</style>
  
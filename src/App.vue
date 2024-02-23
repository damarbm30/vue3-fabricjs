<script>
import { ref } from 'vue';
import { fabric } from 'fabric';

export default {
  data() {
    return {
      count: 8,
      canvas: null,
      rect: null,
      rectCoords: [],
    };
  },
  mounted() {
    const ref = this.$refs.can;
    this.canvas = new fabric.Canvas(ref);
    this.rect = new fabric.Rect({
      stroke: 'red',
      width: 200,
      height: 200,
      fill: 'transparent',
      strokeWidth: 10,
    });
    this.canvas.add(this.rect);

    this.rectCoords = this.rect.getCoords();
  },
  methods: {
    getCoordinate() {
      console.log(this.rect.getCoords());
    },
  },
};
</script>

<template>
  <div>
    <div :style="{ position: 'relative' }">
      <canvas
        ref="can"
        width="400"
        height="400"
        :style="{ 'z-index': 10, position: 'absolute' }"
      ></canvas>
      <img
        src="https://placehold.co/200"
        :style="{ 'z-index': 1, position: 'absolute', top: '25%', left: '25%' }"
      />
    </div>
    <button @click="getCoordinate">Get coordinate</button>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

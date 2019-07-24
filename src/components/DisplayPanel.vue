<template>
  <v-layout>
    <canvas id="canvas"></canvas>
  </v-layout>
</template>

<script>
import * as THREE from "three";
import OrbitControls from "three-orbitcontrols";

export default {
  name: "DisplayPanel",
  props: {
    displayWidth: Number,
    displayHeight: Number
  },
  data() {
    return {
      canvasDOM: null,
      scene: null,
      camera: null,
      renderer: null,
      helper: null,
      controls: null
    };
  },
  methods: {
    init: function() {
      console.log("init");
      this.canvasDOM = document.getElementById("canvas");
      this.canvasDOM.setAttribute(
        "width",
        this.canvasDOM.parentNode.clientWidth
      );
      this.canvasDOM.setAttribute("height", 600);
      console.log();
      this.scene = new THREE.Scene();
      this.scene.background = new THREE.Color(0xffffff);
      this.camera = new THREE.PerspectiveCamera(
        0.75,
        this.canvasDOM.clientWidth / this.canvasDOM.clientHeight,
        0.1,
        10000
      );
      this.renderer = new THREE.WebGLRenderer({
        canvas: this.canvasDOM,
        antialias: true
      });
      this.renderer.setSize(
        this.canvasDOM.clientWidth,
        this.canvasDOM.clientHeight
      );

      this.camera.position.set(10, 5, 10);

      this.controls = new OrbitControls(this.camera, this.canvasDOM);

      this.helper = new THREE.AxesHelper(1, 1, 1);
      this.scene.add(this.helper);
    },
    animate: function() {
      requestAnimationFrame(this.animate);
      this.renderer.render(this.scene, this.camera);
    }
  },
  mounted() {
    this.init();
    this.animate();
  }
};
</script>

<style scoped>
canvas {
  border-radius: 2px;
  box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
    0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);
}
</style>

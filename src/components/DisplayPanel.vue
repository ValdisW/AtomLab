<template>
  <v-container>
    <v-layout>
      <canvas id="canvas"></canvas>
    </v-layout>
  </v-container>
</template>

<script>
import THREE from "three";
import OrbitControls from "three-orbitcontrols";

export default {
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
      this.canvasDOM = document.getElementById("canvas");
      this.canvasDOM.setAttribute("width", 300);
      this.canvasDOM.setAttribute("height", 300);
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

      this.helper = new THREE.AxesHelper(20, 20, 20);
      this.scene.add(helper);
    },
    animate: function() {
      requestAnimationFrame(this.animate);
      this.renderer.render(this.scene, this.camera);
    }
  },
  mounted() {},
  updated() {
    console.log(this.canvasDOM);
    this.init();
    this.animate();
  }
};
</script>

<style scoped>
</style>

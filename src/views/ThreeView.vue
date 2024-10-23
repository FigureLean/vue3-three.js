<template>
    <div ref="sceneContainer" class="scene-container"></div>
</template>
  
  <script>
  import * as THREE from 'three';
  
  export default {
    name: 'ThreeScene',
    mounted() {
      this.initThree();
    },
    methods: {
      initThree() {
        // 场景
        this.scene = new THREE.Scene();
        
        // 相机
        const aspectRatio = this.$refs.sceneContainer.clientWidth / this.$refs.sceneContainer.clientHeight;
        this.camera = new THREE.PerspectiveCamera(75, aspectRatio, 0.1, 1000);
        this.camera.position.z = 5;
  
        // 渲染器
        this.renderer = new THREE.WebGLRenderer();
        this.renderer.setSize(this.$refs.sceneContainer.clientWidth, this.$refs.sceneContainer.clientHeight);
        this.$refs.sceneContainer.appendChild(this.renderer.domElement);
  
        // 立方体
        const geometry = new THREE.BoxGeometry();
        const material = new THREE.MeshBasicMaterial({ color: 'white' });
        this.cube = new THREE.Mesh(geometry, material);
        this.scene.add(this.cube);
  
        // 渲染
        this.animate();
      },
      animate() {
        requestAnimationFrame(this.animate);
  
        // 旋转立方体
        this.cube.rotation.x += 0.01;
        this.cube.rotation.y += 0.01;
  
        this.renderer.render(this.scene, this.camera);
      }
    }
  };
  </script>
  
  <style>
  .scene-container {
    width: 100%;
    height: 100vh; 
  }
  </style>
  
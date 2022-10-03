<script lang="ts">
	import { onMount } from "svelte";

	// import * as THREE from 'three';
	import {
    Canvas,
    Scene,
    PerspectiveCamera,
    DirectionalLight,
    AmbientLight,
    BoxBufferGeometry,
    Mesh,
    MeshStandardMaterial,
    CubeTexture,
    CubeTextureLoader,
    WebGLRenderer,
  } from "svelthree";

  let cubeGeometry = new BoxBufferGeometry(1, 1, 1);
  let cubeMaterial = new MeshStandardMaterial();
  let newCubeMaterial = new CubeTexture()
  let width, height;

  const rotateCube = (obj) => {
    let rAF = 0;
    let doRotate = false;

    function onStart() {
      startRotating();
    }

    function startRotating() {
      doRotate = true;
      rAF = requestAnimationFrame(rotate);
    }

    function rotate() {
      if (doRotate) {
        obj.rotation.x += 0.01;
        obj.rotation.y += 0.01;
        obj.rotation.z += 0.01;
        rAF = requestAnimationFrame(rotate);
      }
    }

    function onDestroy() {
      doRotate = false;
      cancelAnimationFrame(rAF);
    }

    return {
      onStart: onStart,
      onDestroy: onDestroy,
    };
  };

  let is_landscape: boolean = false;
  onMount(async () => {
    is_landscape = (window.innerWidth > window.innerHeight) ? true: false;
  })
</script>



<div class="h-full w-full flex items-center justify-center" bind:clientWidth="{width}" bind:clientHeight="{height}">
<Canvas let:sti w={is_landscape ? 500:350} h={is_landscape ? 500:350}>

    <Scene {sti} let:scene id="scene1">
  
      <PerspectiveCamera {scene} id="cam1" pos={[0, 0, 2]} lookAt={[0, 0, 0]} />
      <AmbientLight {scene} intensity={1.25} />
      <DirectionalLight {scene} pos={[3, 3, 3]} />
  
      <Mesh
        {scene}
        geometry={cubeGeometry}
        material={cubeMaterial}
        mat={{ roughness: 0.5, metalness: 0.5, color: 0xff3e00 }}
        pos={[0, 0, 0]}
        rot={[0.5, 0.6, 0]}
        scale={[1, 1, 1]} 
        animation={rotateCube}
        aniauto
        />
  
    </Scene>
  
    <WebGLRenderer
      {sti}
      sceneId="scene1"
      camId="cam1"
      config={{ antialias: true, alpha: true }} />
  
  </Canvas>
</div>
<template>
  <q-page class="row items-center justify-evenly">
    <div id="test"></div>
  </q-page>
</template>

<script lang="ts">
import {Vue, Component} from 'vue-property-decorator';
import * as THREE from 'three';

const scene = new THREE.Scene();


@Component({
  components: {}
})
export default class PageIndex extends Vue {
  mounted() {
    let scene = new THREE.Scene();
    let camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);

    let renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    (document.getElementById("test") as any).appendChild(renderer.domElement);


    let geometry = new THREE.BoxGeometry();
    let material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
    let cube = new THREE.Mesh( geometry, material );
    let cube2 = new THREE.Mesh( geometry, material );
    let cube3 = new THREE.Mesh( geometry, material );
    let cube4 = new THREE.Mesh( geometry, material );
    scene.add( cube );
    scene.add( cube2 );
    scene.add( cube3 );
    scene.add( cube4 );



    camera.position.z = 10;
    camera.position.x = 1
    camera.position.y = -1
    camera.rotateY(0.1)
    camera.rotateX(0.1)
let y = 0.01


    function animate() {
      requestAnimationFrame( animate );
      renderer.render( scene, camera );
y+=y
      if(cube.position.y >1)
      y = -0.01

      else if (cube.position.y <0){
        y = 0.01
      }
      cube.position.y = cube.position.y+y ;
      cube2.position.y = cube.position.y+y+0.1 ;
      cube3.position.y = cube.position.y+y+0.2 ;
      cube4.position.y = cube.position.y+y+0.3 ;
      console.log(cube.position.y )
      // cube.rotation.y += 0.01;

    }
    animate();

  }

};
</script>

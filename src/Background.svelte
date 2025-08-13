<script>
  import * as THREE from 'three';
  import { onMount, onDestroy } from 'svelte';

  let canvas;
  let scene, camera, renderer, particles, animationId, backgroundPlane;
  let mouse = new THREE.Vector2(0, 0);

  const PARTICLE_COUNT = 2000;

  function createCircleTexture() {
    const size = 64;
    const canvas = document.createElement('canvas');
    canvas.width = size;
    canvas.height = size;
    const ctx = canvas.getContext('2d');

    const gradient = ctx.createRadialGradient(
      size / 2, size / 2, 0,
      size / 2, size / 2, size / 2
    );
    gradient.addColorStop(0, 'rgba(255,255,255,1)');
    gradient.addColorStop(1, 'rgba(255,255,255,0)');

    ctx.fillStyle = gradient;
    ctx.fillRect(0, 0, size, size);

    const texture = new THREE.Texture(canvas);
    texture.needsUpdate = true;
    return texture;
  }

  onMount(() => {
    scene = new THREE.Scene();

    // Camera
    camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );
    camera.position.z = 5;

    // Renderer
    renderer = new THREE.WebGLRenderer({ canvas, alpha: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(window.devicePixelRatio);

    // Background plane with wave shader
    const bgUniforms = {
      u_time: { value: 0.0 },
      u_color1: { value: new THREE.Color('#0a0a1f') }, // deep dark blue
      u_color2: { value: new THREE.Color('#1a0033') }, // deep purple
    };

    const bgMaterial = new THREE.ShaderMaterial({
      uniforms: bgUniforms,
      vertexShader: `
        varying vec2 vUv;
        void main() {
          vUv = uv;
          gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);
        }
      `,
      fragmentShader: `
        uniform float u_time;
        uniform vec3 u_color1;
        uniform vec3 u_color2;
        varying vec2 vUv;

        void main() {
          float wave = sin(vUv.x * 6.0 + u_time * 0.5) * 0.5 +
                       sin(vUv.y * 4.0 + u_time * 0.8) * 0.5;
          wave *= 0.25; // reduce intensity

          vec3 color = mix(u_color1, u_color2, vUv.y + wave);
          gl_FragColor = vec4(color, 1.0);
        }
      `,
      side: THREE.DoubleSide
    });

    const planeGeo = new THREE.PlaneGeometry(50, 50);
    backgroundPlane = new THREE.Mesh(planeGeo, bgMaterial);
    backgroundPlane.position.z = -10;
    scene.add(backgroundPlane);

    // Particles geometry
    const geometry = new THREE.BufferGeometry();
    const positions = [];
    const colors = [];

    const color1 = new THREE.Color('#ff7b00'); // orange
    const color2 = new THREE.Color('#a020f0'); // purple
    const color3 = new THREE.Color('#001f3f'); // dark blue

    for (let i = 0; i < PARTICLE_COUNT; i++) {
      const x = (Math.random() - 0.5) * 10;
      const y = (Math.random() - 0.5) * 10;
      const z = (Math.random() - 0.5) * 10;
      positions.push(x, y, z);

      const mixed = color1.clone().lerp(color2, Math.random()).lerp(color3, Math.random());
      colors.push(mixed.r, mixed.g, mixed.b);
    }

    geometry.setAttribute('position', new THREE.Float32BufferAttribute(positions, 3));
    geometry.setAttribute('color', new THREE.Float32BufferAttribute(colors, 3));

    const material = new THREE.PointsMaterial({
      size: 0.08,
      vertexColors: true,
      transparent: true,
      opacity: 0.85,
      map: createCircleTexture(),
      alphaTest: 0.01
    });

    particles = new THREE.Points(geometry, material);
    scene.add(particles);

    // Mouse move
    window.addEventListener('mousemove', (event) => {
      mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
      mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;
    });

    // Resize
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });

    // Animate
    function animate(time) {
      animationId = requestAnimationFrame(animate);

      bgUniforms.u_time.value = time * 0.001;

      particles.rotation.y += 0.0005;
      particles.rotation.x += 0.0003;

      particles.rotation.y += mouse.x * 0.0005;
      particles.rotation.x += mouse.y * 0.0005;

      renderer.render(scene, camera);
    }

    animate();
  });

  onDestroy(() => {
    cancelAnimationFrame(animationId);
    renderer.dispose();
  });
</script>

<style>
  canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1; /* behind everything */
    width: 100%;
    height: 100%;
    display: block;
  }
</style>

<canvas bind:this={canvas}></canvas>

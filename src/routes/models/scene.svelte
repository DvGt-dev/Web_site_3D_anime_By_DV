<script lang="ts">
	import { T, useFrame } from '@threlte/core'
	import { OrbitControls, useGltf } from '@threlte/extras'
	import Bloom from './bloom.svelte'


	let y = 2
	let rotation = 0

	function levitate() {
		const time = Date.now() / 1000
		const speed = 1
		const offset = 3
		y = Math.sin(time * speed) + offset
		requestAnimationFrame(levitate)
	}

	useFrame((_, delta) => {
		rotation += delta * 0.4
	})

	levitate()
</script>

<Bloom /> 

<!-- <Spaceship/> -->

<T.OrthographicCamera position={[10, 10, 10]} zoom={40} makeDefault>
	<!-- Controls -->
	<OrbitControls enableDamping />
</T.OrthographicCamera>

<T.AmbientLight color="#0000ff" intensity={10} />
<T.PointLight intensity={2} position={[4, 2, 4]} color="#76aac8" />

{#await useGltf('/assets/ghost.glb') then ghost}
	<T is={ghost.scene} position={[0, y, 0]} scale={0.4} />
{/await}

{#await useGltf('/assets/garden.glb') then garden}
	<T is={garden.scene} rotation.y={rotation} />
{/await}



<!-- {#await useGltf('/assets/nissan.glb') then nissan}
	<T is={nissan.scene} position={[-2, y, 0]} scale={0.4} />
{/await}

{#await useGltf('/assets/spaceship.glb') then spaceship}
	<T is={spaceship.scene} position={[0, y, 0]} scale={0.4} />
{/await} -->

<!-- {#await useGltf('/assets/DcYcU.glb') then DcYcU}
	<T is={DcYcU.scene} position={[0, y, 2]} scale={0.4} />
{/await} -->
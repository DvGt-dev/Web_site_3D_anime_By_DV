<script lang="ts">
	import {
		BloomEffect,
		EffectComposer,
		EffectPass,
		KernelSize,
		RenderPass,
		SMAAEffect,
		SMAAPreset,
	} from 'postprocessing'
	import { useRender, useThrelte } from '@threlte/core'

	const { scene, renderer, camera } = useThrelte()
	const composer = new EffectComposer(renderer)

	const setupEffectComposer = (camera: THREE.Camera) => {
		composer.removeAllPasses()
		composer.addPass(new RenderPass(scene, camera))
		composer.addPass(
			new EffectPass(
				camera,
				new SMAAEffect({
					preset: SMAAPreset.HIGH,
					kernelSize: KernelSize.HIGH,
				}),
			),
		)
		composer.addPass(
			new EffectPass(
				camera,
				new BloomEffect({
					kernelSize: KernelSize.MEDIUM,
					luminanceThreshold: 0.5,
					intensity: 1.5,
				}),
			),
		)
	}

	useRender(() => {
		composer.render()
	})

	$: setupEffectComposer(camera)
</script>
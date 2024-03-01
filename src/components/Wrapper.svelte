<script lang="ts">
	import Lenis from '@studio-freight/lenis';
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';
	import { twMerge } from 'tailwind-merge';

	export let wrapperClass = '';
	export let contentClass = '';
	export let infinite = false;

	const randomId = Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);

	onMount(() => {
		const wrapper = document.querySelector<HTMLElement>('#scroll-wrapper-' + randomId)!;
		const content = document.querySelector<HTMLElement>('#scroll-wrapper-' + randomId)!;

		const lenis = new Lenis({
			wrapper,
			content,
			duration: 2,
			infinite
		});

		function raf(time: number) {
			lenis.raf(time);
			requestAnimationFrame(raf);
		}

		const frame = requestAnimationFrame(raf);

		return () => {
			lenis.scrollTo(0, { lerp: 1 });
			lenis.destroy();
			cancelAnimationFrame(frame);
		};
	});
</script>

<div id="scroll-wrapper-{randomId}" class={twMerge('h-[calc(100dvh-8rem)] overflow-y-auto', wrapperClass)}>
	<div in:fly={{ y: -60, duration: 500, delay: 500 }} out:fly={{ y: 60, duration: 500 }} id="scroll-content-{randomId}" class={twMerge('p-8', contentClass)}>
		<slot />
	</div>
</div>

<script lang="ts">
import Lenis from '@studio-freight/lenis';
import { onMount } from 'svelte';
import { twMerge } from 'tailwind-merge';

export let wrapperClass = '';
export let contentClass = '';
export let header = '';
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
	<div id="scroll-content-{randomId}" class={twMerge('p-8', contentClass)}>
		{#if header}
			<h1 id={header.toLocaleLowerCase().replace(' ', '-')} class="scroll-mt-8">{header}</h1>
		{/if}
		<slot />
	</div>
</div>

<script>
	import Wrapper from '$components/Wrapper.svelte';
</script>

<Wrapper wrapperClass="hide-scroll h-auto w-full md:col-span-2 md:h-[calc(100dvh-8rem)] md:w-[calc(100%-340px)] md:shrink-0" infinite={true}>
	<h2 class="m-0 break-all text-center text-6xl font-black uppercase sm:text-9xl">
		{#each new Array(100) as _}
			<span class="odd:text-gray-400 even:text-white">PROJECT </span>
		{/each}
	</h2>
</Wrapper>

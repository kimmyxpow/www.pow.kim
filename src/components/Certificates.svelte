<script lang="ts">
	import Icon from '@iconify/svelte';

	let isProfessional = true;
</script>

<div class="not-prose space-y-8">
	<div class="grid grid-cols-2 overflow-hidden rounded-xl">
		<button
			class="flex items-center justify-center gap-1 py-4 font-bold transition-all duration-200 md:text-lg {isProfessional
				? 'bg-gray-700'
				: 'bg-gray-800 hover:bg-gray-700'}"
			on:click={() => (isProfessional = true)}
		>
			<Icon icon="ph:seal-check-bold" class="text-xl" />
			Professional
		</button>
		<button
			class="md:text-l flex items-center justify-center gap-1 py-4 font-bold transition-all duration-200 {!isProfessional
				? 'bg-gray-700'
				: 'bg-gray-800 hover:bg-gray-700'}"
			on:click={() => (isProfessional = false)}
		>
			<Icon icon="uil:check-circle" class="text-xl" />
			Others
		</button>
	</div>
	{#if isProfessional}
		<enhanced:img class="rounded-xl" src="/img/certificates/professional/1.webp" alt="Sertificate" />
	{:else}
		<div class="gap-2 space-y-2 sm:columns-2 md:columns-3">
			{#each new Array(38) as _, i}
				<enhanced:img class="break-inside-avoid-column rounded-xl" src="/img/certificates/{i + 1}.webp" alt="Sertificate {i + 1}" />
			{/each}
		</div>
	{/if}
</div>

<script lang="ts">
	import Icon from '@iconify/svelte';
	import { clickoutside } from '@svelte-put/clickoutside';

	let isOpen = false;
</script>

<div class="relative" use:clickoutside on:clickoutside={() => (isOpen = false)}>
	<button
		on:click={() => (isOpen = !isOpen)}
		class="grid size-10 place-items-center rounded-lg bg-gradient-to-br from-accent-600 to-secondary-500 transition-all hover:-translate-y-2 hover:scale-110"
	>
		<Icon icon="solar:widget-6-linear" class="size-6 text-white" />
	</button>
	<div
		class="absolute bottom-0 mb-14 flex h-16 min-w-max items-center rounded-xl border border-accent-600 bg-black/20 px-4 text-white backdrop-blur-xl transition-all duration-300 ${isOpen
			? 'pointer-events-auto translate-y-0 opacity-100'
			: 'pointer-events-none -translate-y-6 opacity-0'}"
	>
		<img src="/img/pic.jpeg" alt="Lynette" class="size-12 rounded-full" />
		<span class="mx-2">Lynette</span>
		<button>
			<Icon icon="solar:power-linear" class="size-6 shrink-0 text-secondary-500" />
		</button>
	</div>
</div>

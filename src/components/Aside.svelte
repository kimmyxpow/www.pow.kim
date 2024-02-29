<script lang="ts">
	import Icon from '@iconify/svelte';
	import { page } from '$app/stores';
	import LenisWrapper from './Wrapper.svelte';

	let isOpen = false;

	const links = [
		{
			name: 'About',
			url: '/about',
			icon: 'solar:sticker-smile-circle-2-broken'
		},
		{
			name: 'Project',
			url: '/project',
			icon: 'solar:code-square-broken'
		}
	];

	const social = [
		{
			name: 'chat@pow.kim',
			url: 'mailto:chat@pow.kim',
			icon: 'uil:envelope'
		},
		{
			name: '@powdotkim',
			url: 'https://github.com/powdotkim',
			icon: 'pajamas:github'
		},
		{
			name: '@powdotkim',
			url: 'https://www.instagram.com/powdotkim',
			icon: 'mdi:instagram'
		},
		{
			name: '@powdotkim',
			url: 'https://x.com/powdotkim',
			icon: 'ri:twitter-x-fill'
		},
		{
			name: '@powdotkim',
			url: 'https://www.youtube.com/@powdotkim',
			icon: 'simple-line-icons:social-youtube'
		},
		{
			name: '@powdotkim',
			url: 'https://tiktok.com/@powdotkim',
			icon: 'simple-icons:tiktok'
		},
		{
			name: '@powdotkim',
			url: 'https://www.threads.net/@powdotkim',
			icon: 'akar-icons:threads-fill'
		}
		// {
		// 	name: 'abinovalfauzi',
		// 	url: 'https://www.linkedin.com/in/abinovalfauzi',
		// 	icon: 'mdi:linkedin'
		// }
	];
</script>

<LenisWrapper
	wrapperClass="shrink-0 h-[calc(100dvh-8rem)] min-w-[300px] max-w-[300px] border-r border-gray-800 lg:relative absolute lg:translate-x-0 bg-black z-30 transition-all duration-300 {isOpen
		? 'translate-x-0'
		: '-translate-x-full'}"
	contentClass="space-y-8"
>
	<h1 class="inline-block font-black uppercase text-gray-400">Welcome</h1>
	<p class="font-medium text-gray-300">
		Hello World! Step into this digital space where lines of code come to life. Take a virtual seat and let's dive into the captivating realm of software
		together.
	</p>
	<div class="grid gap-2">
		{#each links as link}
			{@const isCurrent = $page.url.pathname.startsWith(link.url)}
			<a
				on:click={() => (isOpen = false)}
				href={link.url}
				class="group flex items-center gap-2 rounded-2xl border-2 border-gray-800 p-4 text-left text-lg font-bold uppercase text-gray-300 transition-all duration-300 {isCurrent
					? 'bg-gray-800'
					: 'hover:bg-gray-800'}"
			>
				<Icon icon={link.icon} class="text-2xl" />
				{link.name}
				<Icon
					icon="solar:arrow-right-broken"
					class="ml-auto text-4xl transition-all duration-300 {isCurrent
						? 'translate-x-0 opacity-100'
						: '-translate-x-10 opacity-0 group-hover:translate-x-0 group-hover:opacity-100'}"
				/>
			</a>
		{/each}
	</div>
	<span class="inline-block font-black uppercase text-gray-400">Social</span>
	<div class="grid divide-y last:border-b">
		{#each social as link}
			<a href={link.url} target="_blank" class="flex items-center gap-2 py-4 text-lg text-gray-400 first:border-t last:border-b hover:text-white">
				<Icon icon={link.icon} class="text-2xl" />
				{link.name}
				<Icon icon="line-md:external-link-rounded" class="ml-auto text-2xl" />
			</a>
		{/each}
	</div>
</LenisWrapper>
<button
	class="absolute inset-0 z-10 bg-black/20 backdrop-blur transition-all duration-300 {isOpen ? 'opacity-100' : 'pointer-events-none opacity-0'}"
	on:click={() => (isOpen = false)}
>
	<span class="sr-only">Close Sidebar</span>
</button>
<button
	on:click={() => (isOpen = true)}
	class="fixed bottom-16 right-0 flex h-12 items-center gap-2 rounded-tl-xl border-l border-t border-gray-700 bg-black p-4 lg:hidden"
>
	<Icon icon={'ri:menu-5-line'} />
	Open Sidebar
</button>

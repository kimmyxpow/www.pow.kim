<script>
	import Aside from '$components/Aside.svelte';
	import Footer from '$components/Footer.svelte';
	import Header from '$components/Header.svelte';
</script>

<div class="flex h-dvh max-h-dvh min-h-dvh flex-col overflow-hidden bg-black">
	<Header />
	<div class="relative z-0 flex h-full py-16">
		<Aside />
		<div class="prose prose-invert w-full max-w-none prose-img:rounded-xl prose-img:border prose-img:border-gray-700">
			<slot />
		</div>
	</div>
	<Footer />
</div>

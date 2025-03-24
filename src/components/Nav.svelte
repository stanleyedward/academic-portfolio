<script>
	import Toggle from './Buttons/Toggle.svelte';
	export let NavData, defaultAsset, darkMode;
	const { title, links, icon, separator } = NavData;

	const img_url = `/images/${icon || defaultAsset}`;
	let isMenuOpen = false; // State to manage the hamburger menu

	const toggleMenu = () => {
		isMenuOpen = !isMenuOpen;
	};
</script>

<nav
	class="bg-zinc-100 p-6 z-10 border-b dark:bg-[#1c1e20] dark:border-neutral-700 dark:text-zinc-300"
>
	<div class="container mx-auto max-w-7xl flex justify-between items-center">
		<div class="flex items-center gap-4">
			{#if icon}
				<img src={img_url} alt="logo" class="w-14 h-14 rounded-full" />
			{/if}
			<a class="text-gray-500 text-lg font-bold link-hover-border" href="/">{title}</a>
		</div>
		<div class="flex items-center gap-4 md:hidden">
			{#if darkMode !== undefined}
				<Toggle />
			{/if}
			<button on:click={toggleMenu} class="text-gray-500 focus:outline-none">
				<svg
					class="w-6 h-6"
					fill="none"
					stroke="currentColor"
					viewBox="0 0 24 24"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M4 6h16M4 12h16m-7 6h7"
					></path>
				</svg>
			</button>
		</div>
		<div class="hidden md:flex gap-4 items-center">
			{#each links as { title, url }, index}
				<a
					class="text-zinc-300 text-lg font-semibold link-hover-border"
					href={url}
					target={url.startsWith('#') ? '' : '_blank'}
					rel={url.startsWith('#') ? '' : 'noopener noreferrer'}>{title}</a
				>
				{#if separator && index !== links.length - 1}
					<span class="text-gray-400">{separator}</span>
				{/if}
			{/each}
			{#if darkMode !== undefined}
				<Toggle />
			{/if}
		</div>
	</div>
	{#if isMenuOpen}
		<div class="md:hidden bg-zinc-100 dark:bg-[#1c1e20] p-4">
			{#each links as { title, url }, index}
				<a
					class="block text-zinc-300 text-lg font-semibold link-hover-border my-2"
					href={url}
					target={url.startsWith('#') ? '' : '_blank'}
					rel={url.startsWith('#') ? '' : 'noopener noreferrer'}>{title}</a
				>
			{/each}
		</div>
	{/if}
</nav>

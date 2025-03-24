<script>
	import Toggle from './Buttons/Toggle.svelte';
    export let NavData, defaultAsset, darkMode;
    const { title, links, icon, separator } = NavData;

    const img_url = `/images/${icon || defaultAsset}`;
</script>

<!-- <nav
    class="bg-zinc-100 p-6 z-10 border-b dark:bg-[#1c1e20] dark:border-neutral-700 dark:text-zinc-300"
>
    <div class="container mx-auto max-w-7xl flex justify-between gap-10">
        <div class="flex items-center gap-4">
            {#if icon}
                <img src={img_url} alt="logo" class="w-14 h-14 rounded-full" />
            {/if}
            <a class="text-gray-500 text-lg font-bold link-hover-border" href="/">{title}</a>
        </div>
        <div class="flex gap-4 items-center">
            {#each links as { title, url }, index}
                <a
                    class="text-zinc-300 text-lg font-semibold link-hover-border"
                    href={url}
                    target={url.startsWith('#') ? '' : '_blank'}
                    rel={url.startsWith('#') ? '' : 'noopener noreferrer'}
                >{title}</a>
                {#if separator && index !== links.length - 1}
                    <span class="text-gray-400">{separator}</span>
                {/if}
            {/each}
			{#if darkMode !== undefined}
                <Toggle />
            {/if}
        </div>
    </div>
</nav> -->

<nav class="bg-zinc-100 p-4 md:p-6 z-10 border-b dark:bg-[#1c1e20] dark:border-neutral-700 dark:text-zinc-300 w-full sticky top-0">
  <div class="container mx-auto px-4 flex items-center">
    <div class="flex items-center gap-2 md:gap-4">
      {#if icon}
        <img src={img_url} alt="logo" class="w-10 h-10 md:w-14 md:h-14 rounded-full" />
      {/if}
      <a class="text-gray-500 text-base md:text-lg font-bold link-hover-border" href="/">{title}</a>
    </div>
    
    <div class="flex gap-2 md:gap-4 items-center ml-8 md:ml-6 flex-grow justify-end">
      {#each links as { title, url }, index}
        <a
          class="text-zinc-300 text-sm md:text-lg font-semibold link-hover-border whitespace-nowrap"
          href={url}
          target={url.startsWith('#') ? '' : '_blank'}
          rel={url.startsWith('#') ? '' : 'noopener noreferrer'}
        >{title}</a>
        {#if separator && index !== links.length - 1}
          <span class="text-gray-400 hidden md:inline">{separator}</span>
        {/if}
      {/each}
      {#if darkMode !== undefined}
        <Toggle />
      {/if}
    </div>
  </div>
</nav>
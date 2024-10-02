<script>

	import { page } from '$app/stores';
	let tabs = [
    { name: 'Home', path: '/' },
    { name: 'Loan', path: '/' },
    { name: 'Tax', path: '/tax' }
  ];
  let currentRoute = $derived($page.url.pathname);
  let showMenu = $state(false);

  
</script>

<header>
	<nav class="flex items-center border-b border-zinc-700 p-4 lg:px-6">
		<div class="ml-auto flex items-center">
			<button
			  onclick={() => {
				showMenu = true;
			  }}
			  aria-label="Open menu"
			  class="lg:hidden font-bold text-2xl"
			>
			  {showMenu? 'X':'Menu'}
			</button>
		</div>
		{#if showMenu}
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
		onclick={() => {
			showMenu = false;
		}}
		class="absolute inset-0 z-50 flex max-h-screen w-full justify-end overflow-hidden lg:hidden"
		>
			<div class="z-30 w-full bg-white/80  p-6 md:w-1/2 lg:w-1/3">
				
				<div class="mt-6 flex w-full flex-col items-end">
					{#each tabs as tab, i (tab.name)}
						<div
						class:active={currentRoute === tab.path}
						onclick={() => {
							showMenu = false;
						}}
						>
						<a
							data-sveltekit-prefetch
							href={tab.path}
							class={`hover:opacity-100 px-2 py-1  font-bold text-xl rounded-lg ${
							currentRoute === tab.path ? 'opacity-100' : 'opacity-75'
							}`}>{tab.name}</a
						>
						</div>
					{/each}
				</div>
			</div>
		</div>
		{/if}
	</nav>
</header>

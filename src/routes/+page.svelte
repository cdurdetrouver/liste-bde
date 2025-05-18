<script lang="ts">
	import { fly } from 'svelte/transition';
	let selected: string | null = null;

	type user = {
		login: string;
		img: string;
	};

	const hexhaven_bureau: user[] = [
		{
			login: 'tblochet',
			img: 'https://cdn.intra.42.fr/users/06ee31b9d3b096a291e473501ac23f78/tblochet.jpg'
		},
		{
			login: 'agiguair',
			img: 'https://cdn.intra.42.fr/users/ca4456111961e80afb8b3d75a1d70e60/agiguair.jpg'
		},
		{
			login: 'rparodi',
			img: 'https://cdn.intra.42.fr/users/b916de5c0fca8d42e7b67550a1c6b190/rparodi.jpg'
		},
		{
			login: 'jealefev',
			img: 'https://cdn.intra.42.fr/users/26cc88c3c51d4da040f152f76d7889f7/jealefev.jpg'
		},
		{
			login: 'sben-tay',
			img: 'https://cdn.intra.42.fr/users/9ab96e91e551439689894e073f5562a3/sben-tay.jpg'
		}
	];
	const hexhaven_membre: user[] = [
		{
			login: 'liperez',
			img: 'https://cdn.intra.42.fr/users/fc313d9745670001df65ceb00aa755bc/liperez.jpg'
		},
		{
			login: 'tlonghin',
			img: 'https://cdn.intra.42.fr/users/7395d4cb8cdff24319d96755ca64c2f8/tlonghin.jpg'
		},
		{
			login: 'chdoe',
			img: 'https://cdn.intra.42.fr/users/498e20daea035b862c2248d5b76183d9/chdoe.jpg'
		},
		{
			login: 'lgarfi',
			img: 'https://cdn.intra.42.fr/users/df3cf1e332ec6b85632609de1a27cf1d/lgarfi.jpg'
		},
		{
			login: 'tstephan',
			img: 'https://cdn.intra.42.fr/users/4aec95847b488501cb67de7c1dcf3a15/tstephan.jpg'
		},
		{
			login: 'yandry',
			img: 'https://cdn.intra.42.fr/users/71191da9df49e34f404c6fb444390eaa/yandry.jpg'
		},
		{
			login: 'ncrombez',
			img: 'https://cdn.intra.42.fr/users/4017bfb11305c561da5aa2ec39ccc222/ncrombez.jpg'
		}
	];

	const wextrahot_bureau: user[] = [
		{
			login: 'sconiat',
			img: 'https://cdn.intra.42.fr/users/1a3c7e83e63f1537a46fad6ac186a4cc/sconiat.jpg'
		},
		{
			login: 'ramahrez',
			img: 'https://cdn.intra.42.fr/users/1bfa0d4f124c94bd3444025d0e95b8b5/ramahrez.jpg'
		}
	];
	const wextrahot_membre: user[] = [
		{
			login: 'pduhamel',
			img: 'https://cdn.intra.42.fr/users/fd824485d96870193a5de417f01904ad/pduhamel.jpg'
		},
		{
			login: 'ahenault',
			img: 'https://cdn.intra.42.fr/users/67eba95c743a4cfe3636ff0f8e911a83/ahenault.jpg'
		}
	];

	function choose(side: string) {
		selected = side;
	}

	function goBack() {
		selected = null;
	}
</script>

<div class="size-full">
	{#if !selected}
		<div
			class="relative flex h-screen w-full flex-col items-center justify-center overflow-hidden md:flex-row"
		>
			<div
				class="absolute top-0 left-0 z-[-1] h-1/2 w-full bg-[#EC4067] md:top-0 md:h-full md:w-1/2"
			></div>

			<div
				class="absolute top-1/2 left-0 z-[-1] h-1/2 w-full bg-[#131c22] md:top-0 md:left-1/2 md:h-full md:w-1/2"
			></div>

			<div
				class="pointer-events-none relative z-10 flex h-full w-full flex-col items-center justify-center md:flex-row"
			>
				<!-- svelte-ignore a11y_click_events_have_key_events -->
				<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
				<img
					src="/hex-haven.jpg"
					alt="Left Logo"
					class="pointer-events-auto m-4 w-32 max-w-[25vw] cursor-pointer object-contain sm:w-40 md:w-1/4"
					on:click={() => choose('left')}
				/>

				<img src="/bataille.png" alt="VS Logo" class="z-10 my-4 w-16 sm:w-20 md:mx-8" />

				<!-- svelte-ignore a11y_click_events_have_key_events -->
				<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
				<img
					src="/wextra-hot.svg"
					alt="Right Logo"
					class="pointer-events-auto m-4 w-32 max-w-[25vw] cursor-pointer object-contain sm:w-40 md:w-1/4"
					on:click={() => choose('right')}
				/>
			</div>
		</div>
	{:else}
		<div
			class="size-full overflow-y-auto {selected === 'left'
				? 'bg-[#EC4067]'
				: 'bg-[#131c22]'} flex items-center justify-center"
			in:fly={{
				x: selected === 'right' ? window.innerWidth / 2 : -window.innerWidth / 2,
				duration: 500
			}}
			out:fly={{ x: 0, y: -10, duration: 300 }}
		>
			{#if selected === 'left'}
				<div class="mt-50 flex size-full max-w-[90vw] flex-col items-center gap-20">
					<img src="/hex-haven.jpg" alt="Left Logo" class="w-1/4" />
					<div class="flex flex-col items-center gap-4 text-center">
						<h1 class="h1">Hex Haven</h1>
						<p>
							Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor<br />
							incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud<br
							/>
							exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure<br
							/>
							dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.<br
							/>
							Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt<br
							/>
							mollit anim id est laborum.
						</p>
					</div>
					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Bureau</h2>
						<div class="grid gap-4 md:grid-cols-3">
							{#each hexhaven_bureau as user}
								<a
									class="card preset-filled-surface-100-900 border-surface-200-800 card-hover divide-surface-200-800 block max-w-md divide-y overflow-hidden border-[1px]"
									href="https://profile.intra.42.fr/users/{user.login}"
									target="_blank"
								>
									<header>
										<img
											src={user.img}
											alt={user.login}
											class="aspect-square w-full"
											loading="lazy"
										/>
									</header>
									<article class="pt-4 pb-4">
										<h4 class="h4">{user.login}</h4>
									</article>
								</a>
							{/each}
						</div>
					</div>

					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Membres</h2>
						<div class="grid gap-4 md:grid-cols-3">
							{#each hexhaven_membre as user}
								<a
									class="card preset-filled-surface-100-900 border-surface-200-800 card-hover divide-surface-200-800 block max-w-md divide-y overflow-hidden border-[1px]"
									href="https://profile.intra.42.fr/users/{user.login}"
									target="_blank"
								>
									<header>
										<img
											src={user.img}
											alt={user.login}
											class="aspect-square w-full"
											loading="lazy"
										/>
									</header>
									<article class="pt-4 pb-4">
										<h4 class="h4">{user.login}</h4>
									</article>
								</a>
							{/each}
						</div>
					</div>
				</div>
			{:else}
				<div class="mt-50 flex size-full max-w-[90vw] flex-col items-center gap-20">
					<img src="/wextra-hot-no-title.svg" alt="Left Logo" class="w-1/4" />
					<div class="flex flex-col items-center gap-4 text-center">
						<h1 class="h1">-Wextra-Hot</h1>
						<p>
							Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor<br />
							incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud<br
							/>
							exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure<br
							/>
							dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.<br
							/>
							Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt<br
							/>
							mollit anim id est laborum.
						</p>
					</div>
					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Bureau</h2>
						<div class="grid gap-4 md:grid-cols-3">
							{#each wextrahot_bureau as user}
								<a
									class="card preset-filled-surface-100-900 border-surface-200-800 card-hover divide-surface-200-800 block max-w-md divide-y overflow-hidden border-[1px]"
									href="https://profile.intra.42.fr/users/{user.login}"
									target="_blank"
								>
									<header>
										<img
											src={user.img}
											alt={user.login}
											class="aspect-square w-full"
											loading="lazy"
										/>
									</header>
									<article class="pt-4 pb-4">
										<h4 class="h4">{user.login}</h4>
									</article>
								</a>
							{/each}
						</div>
					</div>

					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Membres</h2>
						<div class="grid gap-4 md:grid-cols-3">
							{#each wextrahot_membre as user}
								<a
									class="card preset-filled-surface-100-900 border-surface-200-800 card-hover divide-surface-200-800 block max-w-md divide-y overflow-hidden border-[1px]"
									href="https://profile.intra.42.fr/users/{user.login}"
									target="_blank"
								>
									<header>
										<img
											src={user.img}
											alt={user.login}
											class="aspect-square w-full"
											loading="lazy"
										/>
									</header>
									<article class="pt-4 pb-4">
										<h4 class="h4">{user.login}</h4>
									</article>
								</a>
							{/each}
						</div>
					</div>
				</div>
			{/if}
			<button
				class="absolute top-4 right-4 rounded bg-gray-800 px-4 py-2 text-white"
				on:click={goBack}
			>
				Retour
			</button>
		</div>
	{/if}
</div>

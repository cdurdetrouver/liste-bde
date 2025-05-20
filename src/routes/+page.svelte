<script lang="ts">
	import { fly } from 'svelte/transition';
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';
	import { get } from 'svelte/store';
	let selected: string | null = null;

	$: {
		const url = get(page).url;
		const liste = url.searchParams.get('liste');
		if (liste === 'WextraHot') {
			selected = 'right';
		} else if (liste === 'HexHaven') {
			selected = 'left';
		} else if (liste !== null) {
			// Remove the "liste" param from the URL
			const params = new URLSearchParams(url.searchParams);
			params.delete('liste');
			goto(`${url.pathname}${params.toString() ? '?' + params.toString() : ''}`, {
				replaceState: true
			});
		}
	}

	type user = {
		login: string;
		img: string;
		role?: string;
	};

	const hexhaven_bureau: user[] = [
		{
			login: 'tblochet',
			img: 'https://cdn.intra.42.fr/users/06ee31b9d3b096a291e473501ac23f78/tblochet.jpg',
			role: 'Président'
		},
		{
			login: 'agiguair',
			img: 'https://cdn.intra.42.fr/users/ca4456111961e80afb8b3d75a1d70e60/agiguair.jpg',
			role: 'Vice-Président'
		},
		{
			login: 'rparodi',
			img: 'https://cdn.intra.42.fr/users/b916de5c0fca8d42e7b67550a1c6b190/rparodi.jpg',
			role: 'Trésorier'
		},
		{
			login: 'sben-tay',
			img: 'https://cdn.intra.42.fr/users/9ab96e91e551439689894e073f5562a3/sben-tay.jpg',
			role: 'Vice-Trésorier'
		},
		{
			login: 'jealefev',
			img: 'https://cdn.intra.42.fr/users/26cc88c3c51d4da040f152f76d7889f7/jealefev.jpg',
			role: 'Secrétaire'
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
			img: 'https://cdn.intra.42.fr/users/1a3c7e83e63f1537a46fad6ac186a4cc/sconiat.jpg',
			role: 'Présidente'
		},
		{
			login: 'pfranke',
			img: 'https://cdn.intra.42.fr/users/4cd43f78ead53c1289b4fa7d8ee187fa/pfranke.jpg',
			role: 'Trésorier'
		},
		{
			login: 'ahenault',
			img: 'https://cdn.intra.42.fr/users/67eba95c743a4cfe3636ff0f8e911a83/ahenault.jpg',
			role: 'Secrétaire'
		}
	];
	const wextrahot_membre: user[] = [
		{
			login: 'mlemerci',
			img: 'https://cdn.intra.42.fr/users/5c1e235ab49914db3807374769d7373d/mlemerci.jpg',
			role: 'Design'
		},
		{
			login: 'ramahrez',
			img: 'https://cdn.intra.42.fr/users/1bfa0d4f124c94bd3444025d0e95b8b5/ramahrez.jpg',
			role: 'Clubs'
		},
		{
			login: 'leogarci',
			img: 'https://cdn.intra.42.fr/users/5e5c730ab193e3b5f6c46eb0781838b8/leogarci.jpg',
			role: 'Comptabilité'
		},
		{
			login: 'jle-doua',
			img: 'https://cdn.intra.42.fr/users/964c4a559982b3b7540214c548dfacda/jle-doua.jpg',
			role: 'Évent'
		},
		{
			login: 'albaud',
			img: 'https://cdn.intra.42.fr/users/6f2ae96583a2f307669afee06a7fa66f/albaud.jpg',
			role: 'Réseau'
		},
		{
			login: 'sakerken',
			img: 'https://cdn.intra.42.fr/users/89c58532bbc975ee40cb27f6679317db/sakerken.jpg',
			role: 'Alumnis'
		},
		{
			login: 'nfisher',
			img: 'https://cdn.intra.42.fr/users/a9619c18de35131af9e765a2aa5742e9/nfisher.jpg',
			role: 'International'
		},
		{
			login: 'edervise',
			img: 'https://cdn.intra.42.fr/users/5b06a41fe955ee9034fad2928fa6e4fe/edervise.jpg',
			role: 'Partenariats'
		},
		{
			login: 'ytaieb',
			img: 'https://cdn.intra.42.fr/users/4d8ff2c09e78a742e946afa95c67a769/ytaieb.jpg',
			role: 'Cuisine'
		},
		{
			login: 'pduhamel',
			img: 'https://cdn.intra.42.fr/users/fd824485d96870193a5de417f01904ad/pduhamel.jpg',
			role: 'Cuisine'
		},
		{
			login: 'hepompid',
			img: 'https://cdn.intra.42.fr/users/84837593211fd48f67ced16aa5ab4679/hepompid.jpg',
			role: 'Cuisine'
		},
		{
			login: 'alde-abr',
			img: 'https://cdn.intra.42.fr/users/cffa62f4dfc52bcc1756c205ca996f82/alde-abr.jpg',
			role: 'Jeu Vidéo'
		},
		{
			login: 'scambier',
			img: 'https://cdn.intra.42.fr/users/757e959b25ffad351cd1fdfaf5dc3440/scambier.jpg',
			role: 'Jeu Vidéo'
		},
		{
			login: 'rcini-ha',
			img: 'https://cdn.intra.42.fr/users/be4acad0ef1546c37031856a7667c70d/rcini-ha.jpg',
			role: 'Mascotte'
		},
		{
			login: 'aisidore',
			img: 'https://cdn.intra.42.fr/users/606b4c40e22dfa4ead7ebc62c4ac7fc2/aisidore.jpg',
			role: 'Safety'
		},
		{
			login: 'yaabdall',
			img: 'https://cdn.intra.42.fr/users/c645ba3861f2a3ca606bef339c4c958b/yaabdall.jpg',
			role: 'Safety'
		},
		{
			login: 'pfischof',
			img: 'https://cdn.intra.42.fr/users/c654c606765a3adc1107e3a326bcfb18/pfischof.jpg',
			role: 'Safety'
		},
		{
			login: 'gbazin',
			img: 'https://cdn.intra.42.fr/users/e34890271c705dc0ec03703e9b803fcb/gbazin.jpg',
			role: 'Safety'
		},
		{
			login: 'cboma-ya',
			img: 'https://cdn.intra.42.fr/users/d2ea94bbac1ddad7e69e5fac9fc87a2e/cboma-ya.jpg',
			role: 'Safety'
		},
		{
			login: 'mferaoun',
			img: 'https://cdn.intra.42.fr/users/15db0a37589a92a57997e83610c13233/mferaoun.jpg',
			role: 'Safety'
		},
		{
			login: 'bvictoir',
			img: 'https://cdn.intra.42.fr/users/bf6fc4027d3346aaa00d0c5916957c5a/bvictoir.jpg',
			role: 'Safety'
		},
		{
			login: 'kimnguye',
			img: 'https://cdn.intra.42.fr/users/b19c1d70dfb1534a7159fee2961136c9/kimnguye.jpg',
			role: 'Safety'
		},
		{
			login: 'licohen',
			img: 'https://cdn.intra.42.fr/users/6b08b24bb11f72980fa098e84c635a4a/licohen.jpg',
			role: 'Safety'
		},
		{
			login: 'saberton',
			img: 'https://cdn.intra.42.fr/users/d48f8cfeb660a7723577dc1470ddd62f/saberton.jpg',
			role: 'Safety'
		},
		{
			login: 'mapham',
			img: 'https://cdn.intra.42.fr/users/f0b765382e97c8c76304a398b82b5b9e/mapham.jpg',
			role: 'Safety'
		},
		{
			login: 'ele-borg',
			img: 'https://cdn.intra.42.fr/users/005b496712d37d945a6c0bd9172001c3/ele-borg.jpg',
			role: 'Safety'
		},
		{
			login: 'memotyle',
			img: 'https://cdn.intra.42.fr/users/0969521a6fa87d272a9306f07dd63668/memotyle.jpg',
			role: 'Safety'
		},
		{
			login: 'nghaddar',
			img: 'https://cdn.intra.42.fr/users/57e6c1c4fe001aaa6583576ee9e35483/nghaddar.jpg',
			role: 'Volontaire'
		},
		{
			login: 'cmassol',
			img: 'https://cdn.intra.42.fr/users/c9e3c93e61decfb324addd0b79992ec2/cmassol.jpg',
			role: 'Volontaire'
		},
		{
			login: 'matle-br',
			img: 'https://cdn.intra.42.fr/users/6a73d1b9bf752b6ef169fb40bb3c7302/matle-br.jpg',
			role: 'Volontaire'
		},
		{
			login: 'fflamion',
			img: 'https://cdn.intra.42.fr/users/2348534c171a625765503b2a74fc445a/fflamion.jpg',
			role: 'Volontaire'
		},
		{
			login: 'adecauch',
			img: 'https://cdn.intra.42.fr/users/34f7c5480379544a0726b3b3ae2d131b/adecauch.jpg',
			role: 'Volontaire'
		},
		{
			login: 'jarumuga',
			img: 'https://cdn.intra.42.fr/users/4aa36336c25c10308f535e8c0f93df91/jarumuga.jpg',
			role: 'Volontaire'
		},
		{
			login: 'cle-tort',
			img: 'https://cdn.intra.42.fr/users/cc862484ff08003dc1f55f8cd04a48ef/cle-tort.jpg',
			role: 'Volontaire'
		},
		{
			login: 'nbariol-',
			img: 'https://cdn.intra.42.fr/users/daac2bee6a462f8c2360ccf36f0813be/nbariol-.jpg',
			role: 'Volontaire'
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

				<img src="/bataille.png" alt="VS Logo" class="z-10 my-4 mt-16 w-16 sm:w-20 md:mx-8" />

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
						<!-- <p>
							Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor<br />
						</p> -->
					</div>
					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Bureau</h2>
						<div class="grid grid-cols-2 gap-4 md:grid-cols-4 lg:grid-cols-5">
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
									{#if user.role}
										<article class="space-y-2=4 p-4 text-start">
											<h7 class="h7">{user.role}</h7>
											<h4 class="h4">{user.login}</h4>
										</article>
									{:else}
										<article class="py-4 text-center">
											<h4 class="h4">{user.login}</h4>
										</article>
									{/if}
								</a>
							{/each}
						</div>
					</div>

					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Membres</h2>
						<div class="grid grid-cols-2 gap-4 md:grid-cols-4 lg:grid-cols-5">
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
									{#if user.role}
										<article class="space-y-2=4 p-4 text-start">
											<h7 class="h7">{user.role}</h7>
											<h4 class="h4">{user.login}</h4>
										</article>
									{:else}
										<article class="py-4 text-center">
											<h4 class="h4">{user.login}</h4>
										</article>
									{/if}
								</a>
							{/each}
						</div>
					</div>
				</div>
			{:else}
				<div class="mt-50 flex size-full max-w-[90vw] flex-col items-center gap-20">
					<img src="/wextra-hot.svg" alt="Left Logo" class="w-1/4" />
					<div class="flex flex-col items-center gap-4 text-center">
						<p>
							La liste <strong>-Wextra Hot</strong> débarque à 42 pour pimenter tes journées 🔥
							<br />
							Viens déguster ce qu’on t’a préparé <strong>lundi 26 et mercredi 28 mai</strong>,
							supplément sauce -Wextra Hot 🍴 <br />
							Clique ici si tu n’as pas peur de te brûler :
							<a class="anchor" href="https://linktr.ee/wextrahot" target="_blank">
								https://linktr.ee/wextrahot
							</a>
						</p>
					</div>
					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Bureau</h2>
						<div class="grid grid-cols-2 gap-4 md:grid-cols-4 lg:grid-cols-5">
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
									{#if user.role}
										<article class="space-y-2=4 p-4 text-start">
											<h7 class="h7">{user.role}</h7>
											<h4 class="h4">{user.login}</h4>
										</article>
									{:else}
										<article class="py-4 text-center">
											<h4 class="h4">{user.login}</h4>
										</article>
									{/if}
								</a>
							{/each}
						</div>
					</div>

					<div class="flex flex-col items-center gap-4 text-center">
						<h2 class="h2">Membres</h2>
						<div class="grid grid-cols-2 gap-4 md:grid-cols-4 lg:grid-cols-5">
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
									{#if user.role}
										<article class="space-y-2=4 p-4 text-start">
											<h7 class="h7">{user.role}</h7>
											<h4 class="h4">{user.login}</h4>
										</article>
									{:else}
										<article class="py-4 text-center">
											<h4 class="h4">{user.login}</h4>
										</article>
									{/if}
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

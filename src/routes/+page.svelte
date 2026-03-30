<script lang="ts">
	import { resolve } from '$app/paths';
	import aboutBg from '$lib/assets/about-bg.jpg?enhanced';
	import heroBg from '$lib/assets/hero-bg.jpg?enhanced';
	import {
		Award,
		BookOpen,
		Coffee,
		Globe,
		Mail,
		MapPin,
		Menu,
		Phone,
		Star,
		Utensils,
		Wine,
		X
	} from '@lucide/svelte';
	import { fromAction } from 'svelte/attachments';

	let isScrolled = $state(false);
	let mobileMenuOpen = $state(false);

	const navLinks = [
		{ name: 'Despre', sectionId: 'despre' },
		{ name: 'Meniul Casei', sectionId: 'specialitati' },
		{ name: 'Sezonier', sectionId: 'sezonier' },
		{ name: 'Experiențe', sectionId: 'experiente' },
		{ name: 'Recomandări', sectionId: 'recomandari' }
	];

	const classes = [
		{
			desc: 'O infuzie bogată de literatură și limbi străine, perfectă pentru spiritele creative și comunicative. Un preparat clasic, rafinat prin studiul intensiv al limbii engleze.',
			grade: '8.87',
			id: 'A',
			name: 'Filologie intensiv engleză',
			places: 28,
			profile: 'Uman'
		},
		{
			desc: 'Un meniu echilibrat de științe exacte și explorare a naturii, ideal pentru viitorii cercetători și medici. Ingrediente proaspete din biologie, chimie și fizică.',
			grade: '9.25',
			id: 'B',
			name: 'Științe ale naturii',
			places: 28,
			profile: 'Real'
		},
		{
			desc: 'Specialitatea casei în tehnologie, asezonată cu o perspectivă internațională. O combinație sofisticată de logică pură și comunicare globală.',
			grade: '9.12',
			id: 'C',
			name: 'Matematică-informatică bilingv engleză',
			places: 28,
			profile: 'Real'
		},
		{
			desc: 'O porție intensă de algoritmi și programare, pentru mințile analitice pasionate de inovație digitală. Un preparat modern, esențial pentru viitor.',
			grade: '9.10',
			id: 'D',
			name: 'Matematică-informatică intensiv informatică',
			places: 28,
			profile: 'Real'
		},
		{
			desc: 'Rețeta clasică a succesului în științe exacte, combinând logica matematică cu fundamentele informaticii. Simplu, elegant și extrem de eficient.',
			grade: '9.07',
			id: 'E',
			name: 'Matematică-informatică',
			places: 28,
			profile: 'Real'
		}
	];

	const optionals = [
		'Adolescență și autocunoaștere',
		'Astronomie',
		'Educație pentru sănătate',
		'Educație pentru schimbări climatice',
		'Fotografia și comunicarea socială',
		'Marketing personal',
		'Practica traducerii',
		'Problemele lumii contemporane',
		'Tehnologii multimedia',
		'Tehnologii web',
		'Tinerii voleibaliști',
		'Turismul European'
	];

	const experiences = [
		{ desc: 'Arta argumentării servită fierbinte', name: 'C.N.M.K. Debate' },
		{ desc: 'Teatru și voluntariat pentru suflet', name: 'Studio 21' },
		{ desc: 'Modelare și imprimare 3D de ultimă generație', name: 'Club 3D' },
		{ desc: 'Dansuri moderne și populare, un desert dinamic', name: 'Let’s Dance' },
		{ desc: 'Robotică și inovație tehnologică', name: 'Ignition Union' },
		{ desc: 'Grup de inițiativă locală și creativitate', name: 'CNMK Studio' },
		{ desc: 'Armonii vocale rafinate', name: 'Corul Colegiului' },
		{ desc: 'Energie și spirit de echipă', name: 'Ansambluri Sportive' },
		{ desc: '„Portret” și „Sui Generis” - literatură fină', name: 'Revistele Școlii' }
	];

	const certifications = [
		'Diplomă de merit cu titlul de șef de promoție',
		'Certificat de competență lingvistică',
		'Atestat profesional',
		'Permisul Profil ECDL',
		'Permisul Profil ECDL BAC',
		'Certificat Cambridge'
	];

	function handleScroll() {
		isScrolled = window.scrollY > 50;
	}

	function closeMobileMenu() {
		mobileMenuOpen = false;
	}

	function reveal(node: HTMLElement, params: { delay?: number } = {}) {
		const delay = params.delay ?? 0;

		node.style.setProperty('--reveal-delay', `${delay}ms`);

		const observer = new IntersectionObserver(
			(entries) => {
				for (const entry of entries) {
					if (entry.isIntersecting) {
						node.classList.add('revealed');
						observer.unobserve(node);
					}
				}
			},
			{
				rootMargin: '0px 0px -50px 0px',
				threshold: 0.12
			}
		);

		node.classList.add('reveal');
		observer.observe(node);

		return {
			destroy() {
				observer.disconnect();
			}
		};
	}
</script>

<svelte:window on:scroll={handleScroll} />

<div class="min-h-screen bg-[#f7f1e8] text-[#0f172a] selection:bg-[#c8a44d] selection:text-white">
	<nav
		class={[
			'fixed inset-x-0 top-0 z-50 transition-all duration-300',
			{
				'bg-[#0f172a]/95 py-4 shadow-lg backdrop-blur-sm': isScrolled,
				'bg-transparent py-6': !isScrolled
			}
		]}
	>
		<div class="mx-auto flex max-w-7xl items-center justify-between px-6">
			<a href={resolve('/')} class="flex items-center gap-2">
				<img
					src="/logo-modern.svg"
					alt="CNMK Logo"
					class={[
						'h-10 w-auto transition-all duration-300',
						{
							'brightness-0 invert': isScrolled
						}
					]}
				/>
			</a>

			<div class="hidden items-center gap-8 md:flex">
				{#each navLinks as link (link.sectionId)}
					<a
						href={resolve(`/#${link.sectionId}`)}
						class={[
							'text-sm tracking-[0.2em] uppercase transition-colors hover:text-[#c8a44d]',
							{
								'text-[#d7dce5]': !isScrolled,
								'text-[#e8dcc6]': isScrolled
							}
						]}
					>
						{link.name}
					</a>
				{/each}

				<a
					href="#specialitati"
					class="border border-[#c8a44d] px-6 py-2 text-sm tracking-[0.2em] text-[#c8a44d] uppercase transition-colors hover:bg-[#c8a44d] hover:text-white"
				>
					Rezervă
				</a>
			</div>

			<button class="text-[#c8a44d] md:hidden" onclick={() => (mobileMenuOpen = !mobileMenuOpen)}>
				{#if mobileMenuOpen}
					<X class="h-6 w-6" />
				{:else}
					<Menu class="h-6 w-6" />
				{/if}
			</button>
		</div>
	</nav>

	{#if mobileMenuOpen}
		<div class="fixed inset-0 z-40 flex flex-col items-center justify-center gap-8 bg-[#0f172a]">
			{#each navLinks as link (link.sectionId)}
				<a
					href={resolve(`/#${link.sectionId}`)}
					class="font-serif text-2xl text-[#f7f1e8] transition-colors hover:text-[#c8a44d]"
					onclick={closeMobileMenu}
				>
					{link.name}
				</a>
			{/each}
		</div>
	{/if}

	<section class="relative flex min-h-screen items-center justify-center overflow-hidden pt-20">
		<div class="absolute inset-0 z-0">
			<enhanced:img
				src={heroBg}
				alt="CNMK Building"
				class="h-full w-full object-cover object-center"
			/>
			<div class="absolute inset-0 z-10 bg-[#0f172a]/70 mix-blend-multiply"></div>
			<div
				class="absolute inset-0 z-20 bg-linear-to-b from-[#0f172a]/80 via-[#0f172a]/40 to-[#0f172a]"
			></div>
			<div class="grid-background absolute inset-0 z-30 opacity-[0.05]"></div>
		</div>

		<div class="relative z-30 mx-auto max-w-4xl px-6 text-center">
			<div class="animate-in duration-700 zoom-in-95 fade-in">
				<div class="mb-6 flex justify-center">
					<Utensils class="h-12 w-12 text-[#c8a44d] drop-shadow-lg" strokeWidth={1} />
				</div>

				<h2
					class="mb-6 text-sm font-medium tracking-[0.3em] text-[#c8a44d] uppercase drop-shadow-md md:text-base"
				>
					Colegiul Național „Mihail Kogălniceanu” Galați
				</h2>

				<h1
					class="mb-8 font-serif text-5xl leading-tight text-[#f7f1e8] drop-shadow-xl md:text-7xl lg:text-8xl"
				>
					Gustul <br /><span class="text-[#c8a44d] italic">Performanței</span>
				</h1>

				<p
					class="mx-auto mb-12 max-w-2xl text-lg font-light text-[#e8dcc6] drop-shadow-md md:text-xl"
				>
					„Societatea de mâine va fi oglinda școlii de azi!”
				</p>

				<div class="flex flex-col items-center justify-center gap-4 sm:flex-row">
					<a
						href="#specialitati"
						class="w-full bg-[#c8a44d] px-8 py-4 text-sm font-medium tracking-[0.2em] text-[#0f172a] uppercase transition-colors hover:bg-[#f7f1e8] sm:w-auto"
					>
						Descoperă Meniul
					</a>
					<a
						href="#despre"
						class="w-full border border-[#f7f1e8] px-8 py-4 text-sm tracking-[0.2em] text-[#f7f1e8] uppercase transition-colors hover:bg-[#f7f1e8] hover:text-[#0f172a] sm:w-auto"
					>
						Povestea Noastră
					</a>
				</div>
			</div>
		</div>
	</section>

	<section id="despre" class="relative bg-[#0f172a] py-24 text-[#f7f1e8]">
		<div class="mx-auto max-w-6xl px-6">
			<div class="grid items-center gap-16 md:grid-cols-2">
				<div {@attach fromAction(reveal)}>
					<h2 class="mb-6 font-serif text-4xl md:text-5xl">Despre Restaurant</h2>
					<p class="mb-8 text-sm tracking-[0.2em] text-[#c8a44d] uppercase">Tradiție din 1878</p>

					<div class="space-y-6 leading-relaxed font-light text-[#e8dcc6]">
						<p>
							Asemenea unui restaurant fine dining cu o istorie bogată, Colegiul Național „Mihail
							Kogălniceanu” servește excelență educațională de peste un secol. Rețeta noastră
							combină tradiția academică riguroasă cu ingredientele inovației moderne.
						</p>
						<p>
							Fiecare elev care ne trece pragul este tratat ca un oaspete de onoare, primind un
							meniu educațional personalizat, menit să îi hrănească mintea și să îi cultive
							caracterul pentru a deveni un lider al societății de mâine.
						</p>
					</div>

					<div class="mt-12 grid grid-cols-2 gap-8 border-t border-white/10 pt-8">
						<div>
							<div class="mb-2 flex items-center gap-3 text-[#c8a44d]">
								<MapPin class="h-5 w-5" />
								<span class="font-serif text-lg">Locație</span>
							</div>
							<p class="text-sm text-[#e8dcc6]">
								Bulevardul Brăilei nr. 161B<br />
								Galați, România
							</p>
						</div>

						<div>
							<div class="mb-2 flex items-center gap-3 text-[#c8a44d]">
								<Phone class="h-5 w-5" />
								<span class="font-serif text-lg">Rezervări</span>
							</div>
							<p class="text-sm text-[#e8dcc6]">
								0236 430 704<br />
								cnmkgalati@yahoo.ro
							</p>
						</div>
					</div>
				</div>

				<div {@attach fromAction(reveal, () => ({ delay: 150 }))} class="relative h-full">
					<div class="relative aspect-4/5 h-full border border-[#c8a44d]/30 p-4">
						<div class="relative h-full w-full overflow-hidden bg-white/5">
							<enhanced:img
								src={aboutBg}
								alt="Statuie Mihail Kogălniceanu"
								class="h-full w-full object-cover transition-transform duration-700 hover:scale-105"
							/>
							<div class="absolute inset-0 bg-[#0f172a]/10"></div>
						</div>

						<div
							class="absolute -bottom-8 -left-8 z-10 flex h-32 w-32 items-center justify-center rounded-full border-4 border-[#0f172a] bg-[#f7f1e8] p-2 shadow-2xl md:h-40 md:w-40"
						>
							<img
								src="/logo-vechi.svg"
								alt="Sigiliu Tradiție"
								class="h-full w-full object-contain"
							/>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<section id="specialitati" class="bg-[#f7f1e8] py-24">
		<div class="mx-auto max-w-5xl px-6">
			<div class="mb-16 text-center" {@attach fromAction(reveal)}>
				<div class="mb-4 flex justify-center">
					<Star class="h-8 w-8 text-[#c8a44d]" strokeWidth={1.5} />
				</div>
				<h2 class="mb-4 font-serif text-4xl text-[#0f172a] md:text-5xl">Specialitățile Casei</h2>
				<p class="text-sm font-medium tracking-[0.2em] text-[#c8a44d] uppercase">
					Oferta Educațională
				</p>
				<div class="mt-6 flex items-center justify-center gap-4">
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
					<div class="h-2 w-2 rounded-full bg-[#c8a44d]"></div>
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
				</div>
			</div>

			<div class="space-y-12">
				{#each classes as item, index (item.id)}
					<div {@attach fromAction(reveal, () => ({ delay: index * 100 }))}>
						<div
							class="group flex flex-col items-start gap-6 border border-transparent p-6 transition-all duration-500 hover:border-[#c8a44d]/20 hover:bg-white hover:shadow-xl md:flex-row md:gap-12"
						>
							<div
								class="flex h-16 w-16 shrink-0 items-center justify-center rounded-sm bg-[#0f172a] font-serif text-2xl text-[#c8a44d]"
							>
								{item.id}
							</div>

							<div class="grow">
								<div class="mb-2 flex flex-col justify-between gap-2 md:flex-row md:items-baseline">
									<h3
										class="font-serif text-2xl text-[#0f172a] transition-colors group-hover:text-[#c8a44d]"
									>
										{item.name}
									</h3>

									<div class="flex gap-3 text-xs font-medium tracking-wider uppercase">
										<span class="bg-[#e8dcc6] px-2 py-1 text-[#334155]">{item.profile}</span>
										<span class="bg-[#e8dcc6] px-2 py-1 text-[#334155]">{item.places} locuri</span>
									</div>
								</div>

								<p class="mb-4 font-light text-[#475569] italic">{item.desc}</p>

								<div class="flex items-center gap-2 text-sm font-medium text-[#c8a44d]">
									<Star class="h-4 w-4 fill-current" />
									<span>Ultima medie (2025): {item.grade}</span>
								</div>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<section id="sezonier" class="relative overflow-hidden bg-[#0f172a] py-24 text-[#f7f1e8]">
		<div
			class="absolute top-0 left-0 h-px w-full bg-linear-to-r from-transparent via-[#c8a44d] to-transparent opacity-30"
		></div>

		<div class="mx-auto max-w-6xl px-6">
			<div class="mb-16 text-center" {@attach fromAction(reveal)}>
				<div class="mb-4 flex justify-center">
					<BookOpen class="h-8 w-8 text-[#c8a44d]" strokeWidth={1.5} />
				</div>
				<h2 class="mb-4 font-serif text-4xl text-[#f7f1e8] md:text-5xl">Meniu Sezonier</h2>
				<p class="text-sm font-medium tracking-[0.2em] text-[#c8a44d] uppercase">
					Selecție Specială de Opționale
				</p>
				<div class="mt-6 flex items-center justify-center gap-4">
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
					<div class="h-2 w-2 rounded-full bg-[#c8a44d]"></div>
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
				</div>
			</div>

			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
				{#each optionals as optional, index (optional)}
					<div {@attach fromAction(reveal, () => ({ delay: index * 50 }))}>
						<div
							class="group flex h-full cursor-pointer items-center gap-4 border border-white/10 p-4 transition-colors hover:border-[#c8a44d]/50"
						>
							<div
								class="h-2 w-2 rounded-full bg-[#c8a44d] transition-transform group-hover:scale-150"
							></div>
							<span class="font-serif text-lg transition-colors group-hover:text-[#c8a44d]">
								{optional}
							</span>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<section id="experiente" class="bg-[#f7f1e8] py-24">
		<div class="mx-auto max-w-6xl px-6">
			<div class="mb-16 text-center" {@attach fromAction(reveal)}>
				<div class="mb-4 flex justify-center">
					<Coffee class="h-8 w-8 text-[#c8a44d]" strokeWidth={1.5} />
				</div>
				<h2 class="mb-4 font-serif text-4xl text-[#0f172a] md:text-5xl">Experiențe Speciale</h2>
				<p class="text-sm font-medium tracking-[0.2em] text-[#c8a44d] uppercase">
					Recomandările Chef-ului
				</p>
				<div class="mt-6 flex items-center justify-center gap-4">
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
					<div class="h-2 w-2 rounded-full bg-[#c8a44d]"></div>
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
				</div>
			</div>

			<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
				{#each experiences as exp, index (exp.name)}
					<div {@attach fromAction(reveal, () => ({ delay: index * 100 }))}>
						<div
							class="flex items-center gap-6 border-b border-[#d9c9a2]/30 p-4 transition-colors hover:bg-white"
						>
							<div class="text-[#c8a44d]">
								<Wine class="h-6 w-6" strokeWidth={1.5} />
							</div>
							<div>
								<h4 class="font-serif text-xl text-[#0f172a]">{exp.name}</h4>
								<p class="text-sm text-[#475569] italic">{exp.desc}</p>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<section id="recomandari" class="border-t border-[#d9c9a2]/20 bg-[#e8dcc6] py-24">
		<div class="mx-auto max-w-4xl px-6 text-center">
			<div class="mb-16 text-center" {@attach fromAction(reveal)}>
				<div class="mb-4 flex justify-center">
					<Award class="h-8 w-8 text-[#c8a44d]" strokeWidth={1.5} />
				</div>
				<h2 class="mb-4 font-serif text-4xl text-[#0f172a] md:text-5xl">
					Stele Michelin Academice
				</h2>
				<p class="text-sm font-medium tracking-[0.2em] text-[#c8a44d] uppercase">
					Premii, Certificări și Recomandări
				</p>
				<div class="mt-6 flex items-center justify-center gap-4">
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
					<div class="h-2 w-2 rounded-full bg-[#c8a44d]"></div>
					<div class="h-px w-16 bg-[#d9c9a2]"></div>
				</div>
			</div>

			<div class="mt-12 flex flex-wrap justify-center gap-4">
				{#each certifications as cert, index (cert)}
					<div {@attach fromAction(reveal, () => ({ delay: index * 100 }))}>
						<div
							class="flex items-center gap-3 rounded-full border border-[#c8a44d]/20 bg-white px-6 py-3 shadow-sm transition-all hover:border-[#c8a44d] hover:shadow-md"
						>
							<Award class="h-4 w-4 text-[#c8a44d]" />
							<span class="text-sm font-medium text-[#0f172a]">{cert}</span>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<footer class="border-t-4 border-[#c8a44d] bg-[#0f172a] pt-20 pb-10 text-[#f7f1e8]">
		<div class="mx-auto max-w-6xl px-6">
			<div class="mb-16 grid gap-12 text-center md:grid-cols-3 md:text-left">
				<div>
					<img
						src="/logo-modern.svg"
						alt="CNMK Logo"
						class="mx-auto mb-6 h-12 w-auto opacity-90 brightness-0 invert md:mx-0"
					/>
					<p class="text-sm leading-relaxed font-light text-[#e8dcc6]">
						Colegiul Național „Mihail Kogălniceanu” Galați.<br />
						O instituție de prestigiu unde tradiția întâlnește performanța.
					</p>
				</div>

				<div class="flex flex-col items-center md:items-start">
					<h4 class="mb-6 text-xs font-semibold tracking-[0.2em] text-[#c8a44d] uppercase">
						Contact
					</h4>
					<div class="space-y-3 text-sm font-light text-[#e8dcc6]">
						<p class="flex items-center gap-3">
							<MapPin class="h-4 w-4 text-[#c8a44d]" />
							Bulevardul Brăilei nr. 161B
						</p>
						<p class="flex items-center gap-3">
							<Phone class="h-4 w-4 text-[#c8a44d]" />
							0236 430 704
						</p>
						<p class="flex items-center gap-3">
							<Mail class="h-4 w-4 text-[#c8a44d]" />
							cnmkgalati@yahoo.ro
						</p>
						<p class="flex items-center gap-3">
							<Globe class="h-4 w-4 text-[#c8a44d]" />
							www.cnmkgl.ro
						</p>
						<p class="flex items-center gap-3">
							<svg
								viewBox="0 0 24 24"
								aria-hidden="true"
								class="h-4 w-4 shrink-0 fill-current text-[#c8a44d]"
							>
								<path
									d="M22 12a10 10 0 1 0-11.56 9.88v-6.99H7.9V12h2.54V9.8c0-2.5 1.49-3.88 3.77-3.88 1.09 0 2.23.2 2.23.2v2.46h-1.26c-1.24 0-1.63.77-1.63 1.56V12h2.78l-.44 2.89h-2.34v6.99A10 10 0 0 0 22 12"
								/>
							</svg>
							<a
								href="https://www.facebook.com/cnmkgl1876"
								target="_blank"
								rel="noopener noreferrer"
								class="transition-colors hover:text-[#c8a44d]"
							>
								facebook.com/cnmkgl1876
							</a>
						</p>
						<p class="flex items-center gap-3">
							<svg
								viewBox="0 0 24 24"
								aria-hidden="true"
								class="h-4 w-4 shrink-0 fill-current text-[#c8a44d]"
							>
								<path
									d="M7 2C4.24 2 2 4.24 2 7v10c0 2.76 2.24 5 5 5h10c2.76 0 5-2.24 5-5V7c0-2.76-2.24-5-5-5H7Zm0 2h10c1.65 0 3 1.35 3 3v10c0 1.65-1.35 3-3 3H7c-1.65 0-3-1.35-3-3V7c0-1.65 1.35-3 3-3Zm11.5 1.5a1.5 1.5 0 1 0 0 3 1.5 1.5 0 0 0 0-3ZM12 7a5 5 0 1 0 0 10 5 5 0 0 0 0-10Zm0 2a3 3 0 1 1 0 6 3 3 0 0 1 0-6Z"
								/>
							</svg>
							<a
								href="https://www.instagram.com/cnmk_cnmk/"
								target="_blank"
								rel="noopener noreferrer"
								class="transition-colors hover:text-[#c8a44d]"
							>
								instagram.com/cnmk_cnmk
							</a>
						</p>
					</div>
				</div>

				<div class="flex flex-col items-center md:items-start">
					<h4 class="mb-6 text-xs font-semibold tracking-[0.2em] text-[#c8a44d] uppercase">
						Motto
					</h4>
					<p class="font-serif text-lg text-[#e8dcc6] italic">
						„Societatea de mâine va fi oglinda școlii de azi!”
					</p>
				</div>
			</div>

			<div class="border-t border-white/10 pt-10 text-center">
				<p class="mb-4 font-serif text-xl text-[#c8a44d]">
					„În meniul viitorului, excelența este specialitatea casei.”
				</p>
				<p class="text-xs tracking-[0.2em] text-white/50 uppercase">
					© {new Date().getFullYear()} Colegiul Național „Mihail Kogălniceanu” Galați. Toate drepturile
					rezervate.
				</p>
			</div>
		</div>
	</footer>
</div>

<style>
	:global(html) {
		scroll-behavior: smooth;
	}

	.reveal {
		opacity: 0;
		transform: translateY(20px);
		transition:
			opacity 0.6s ease,
			transform 0.6s ease;
		transition-delay: var(--reveal-delay, 0ms);
		will-change: opacity, transform;
	}

	.reveal.revealed {
		opacity: 1;
		transform: translateY(0);
	}

	.grid-background {
		background-image: radial-gradient(#f7f1e8 1px, transparent 1px);
		background-size: 32px 32px;
		-webkit-mask-image: linear-gradient(to bottom, black 0%, transparent 100%);
		mask-image: linear-gradient(to bottom, black 0%, transparent 100%);
	}
</style>

<script lang="ts">
	import '@fontsource-variable/inter/wght.css';
	import '@fontsource-variable/inter/wght-italic.css';
	import '@fontsource-variable/playfair-display/wght.css';
	import '@fontsource-variable/playfair-display/wght-italic.css';

	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Colegiul Național „Mihail Kogălniceanu” Galați | Meniul Excelenței</title>
	<meta
		name="description"
		content="Website de prezentare pentru Colegiul Național „Mihail Kogălniceanu” Galați, într-un concept vizual premium inspirat de un meniu modern de restaurant, pentru târgul de oferte educaționale 2026-2027."
	/>
</svelte:head>
{@render children()}

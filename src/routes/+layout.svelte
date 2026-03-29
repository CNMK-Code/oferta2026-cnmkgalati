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
	<title>Targul de oferta 2026 - CNMK Galati</title>
</svelte:head>
{@render children()}

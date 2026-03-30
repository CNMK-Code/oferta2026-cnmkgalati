<script lang="ts">
	import '@fontsource-variable/inter/wght.css';
	import '@fontsource-variable/inter/wght-italic.css';
	import '@fontsource-variable/playfair-display/wght.css';
	import '@fontsource-variable/playfair-display/wght-italic.css';

	import './layout.css';
	import { PUBLIC_SITE_URL } from '$env/static/public';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();

	const siteUrl = PUBLIC_SITE_URL;
	const pageTitle = 'Colegiul National "Mihail Kogalniceanu" Galati | Oferta Educationala 2026';
	const pageDescription =
		'Website oficial de prezentare pentru oferta educationala CNMK Galati la Targul de Oferta 2026. Profiluri, specialitati, optionale si experiente pentru viitorii liceeni.';
	const ogImage = `${siteUrl}/logo-modern.svg`;
	const jsonLd = JSON.stringify({
		'@context': 'https://schema.org',
		'@type': 'School',
		address: {
			'@type': 'PostalAddress',
			addressCountry: 'RO',
			addressLocality: 'Galati',
			streetAddress: 'Bulevardul Brailei nr. 161B'
		},
		logo: ogImage,
		name: 'Colegiul National "Mihail Kogalniceanu" Galati',
		url: siteUrl
	});
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>{pageTitle}</title>
	<meta name="description" content={pageDescription} />
	<meta name="robots" content="index, follow, max-image-preview:large" />
	<meta name="theme-color" content="#0f172a" />

	<link rel="canonical" href={siteUrl} />

	<meta property="og:type" content="website" />
	<meta property="og:site_name" content="CNMK Galati" />
	<meta property="og:locale" content="ro_RO" />
	<meta property="og:url" content={siteUrl} />
	<meta property="og:title" content={pageTitle} />
	<meta property="og:description" content={pageDescription} />
	<meta property="og:image" content={ogImage} />

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={pageTitle} />
	<meta name="twitter:description" content={pageDescription} />
	<meta name="twitter:image" content={ogImage} />

	<svelte:element this={'script'} type="application/ld+json">{jsonLd}</svelte:element>
</svelte:head>
{@render children()}

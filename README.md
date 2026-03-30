# Oferta CNMK Galati 2026

Site de prezentare pentru participarea Colegiului National "Mihail Kogalniceanu" Galati la Targul de Oferta Educationala 2026.

Aplicatia este construita cu SvelteKit (Svelte 5 + TypeScript), Tailwind CSS si este pregatita pentru rulare in sistem Cloudflare (Workers).

## Tehnologii

- SvelteKit 2 + Svelte 5 (runes mode)
- TypeScript
- Tailwind CSS 4
- Bun (package manager)
- Cloudflare Workers (adapter Cloudflare + Wrangler)

## Instalare

```sh
bun install
```

## Dezvoltare locala

Porneste serverul de dezvoltare:

```sh
bun run dev
```

Comenzi utile:

```sh
bun run check
bun run lint
bun run format
```

## Build

Genereaza build-ul de productie:

```sh
bun run build
```

Previzualizeaza local build-ul:

```sh
bun run preview
```

## Deploy pe Cloudflare

Proiectul foloseste `@sveltejs/adapter-cloudflare`, iar configuratia Wrangler este in `wrangler.json`.

Flux recomandat pentru deploy:

```sh
bun run build
bunx wrangler deploy
```

Asigura-te ca esti autentificat in Cloudflare inainte de deploy:

```sh
bunx wrangler login
```

## Structura continut

Pagina principala include sectiunile de prezentare pentru oferta CNMK 2026:

- Hero de introducere
- Despre colegiu
- Specialitati (profiluri/clase)
- Meniu sezonier (optionale)
- Experiente (cluburi/activitati)
- Recomandari (premii, certificari)

## Licenta

Utilizare interna CNMK pentru comunicare si prezentare institutionala.

<script lang="ts">
	import './layout.css';

	let { children } = $props();
</script>

<svelte:head>
	<title>Blink — Instant Space Switching for macOS</title>
	<meta
		name="description"
		content="Blink makes macOS space switching completely instant. No more 0.5-second animation every time you swipe between spaces. Free and open source."
	/>
	<meta property="og:title" content="Blink — Instant Space Switching for macOS" />
	<meta
		property="og:description"
		content="Blink makes macOS space switching completely instant. Free and open source."
	/>
	<meta name="theme-color" content="#ffffff" />
	<link rel="icon" href="/icon.png" type="image/png" />
</svelte:head>

{@render children()}

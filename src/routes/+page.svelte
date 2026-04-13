<script lang="ts">
	const DOWNLOAD_URL = 'https://github.com/benkoppe/Blink/releases/latest/download/Blink.dmg';
	const GITHUB_URL = 'https://github.com/benkoppe/Blink';
	const BREW_COMMAND = 'brew install --cask benkoppe/tap/blink';

	let brewCopied = $state(false);

	function copyBrew() {
		navigator.clipboard.writeText(BREW_COMMAND);
		brewCopied = true;
		setTimeout(() => {
			brewCopied = false;
		}, 2000);
	}

	const features = [
		{
			title: 'Zero configuration',
			description:
				'Blink immediately takes over your existing ctrl+left/right hotkeys and three/four-finger swipe gestures. Works out of the box.'
		},
		{
			title: 'Works in Mission Control',
			description:
				'The only app that enables instant switching inside Mission Control, not just the standard space view.'
		},
		{
			title: 'Space wrap-around',
			description:
				'Swiping past the last space wraps back to the first, and vice versa. Navigate your spaces as a continuous loop.'
		},
		{
			title: 'Jump to any space',
			description:
				'Assign custom hotkeys to jump directly to a specific space index — no more cycling through one by one.'
		},
		{
			title: 'Under 10 MB',
			description:
				'Blink is a tiny, focused utility. It has virtually no memory footprint and no background impact on your system.'
		},
		{
			title: 'Fully customizable',
			description:
				'Control the menu bar indicator, gesture sensitivity, hotkey mappings, and more from the built-in settings panel.'
		}
	];

	// To add/remove a column: edit `comparisonColumns` only.
	// To add/remove a row: edit `comparisonRows` only.
	const comparisonColumns: { key: string; label: string }[] = [
		{ key: 'instant', label: 'Instant' },
		{ key: 'free', label: 'Free' },
		{ key: 'nativespaces', label: 'Native Spaces' },
		{ key: 'nosip', label: 'No SIP Needed' },
		{ key: 'missioncontrol', label: 'Mission Control' }
	];

	const comparisonRows: { name: string; highlight?: boolean; values: Record<string, boolean> }[] = [
		{
			name: 'Blink',
			highlight: true,
			values: { instant: true, free: true, nativespaces: true, nosip: true, missioncontrol: true }
		},
		{
			name: 'BetterTouchTool',
			values: {
				instant: true,
				free: false,
				nativespaces: true,
				nosip: true,
				missioncontrol: false
			}
		},
		{
			name: 'yabai',
			values: {
				instant: false,
				free: true,
				nativespaces: true,
				nosip: false,
				missioncontrol: false
			}
		},
		{
			name: 'AeroSpace',
			values: {
				instant: true,
				free: true,
				nativespaces: false,
				nosip: true,
				missioncontrol: false
			}
		}
	];
</script>

<!-- NAV -->
<header class="sticky top-0 z-50 border-b border-[#e5e5e5] bg-white">
	<nav class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
		<a href="/" class="flex items-center gap-2.5">
			<img src="/icon.png" alt="Blink icon" class="h-8 w-8 rounded-[10px]" />
			<span class="text-[17px] font-semibold tracking-tight text-[#111]">Blink</span>
		</a>
		<div class="flex items-center gap-3">
			<a
				href={GITHUB_URL}
				target="_blank"
				rel="noopener noreferrer"
				aria-label="View source on GitHub"
				class="text-[#111] hover:text-[#333]"
			>
				<svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
					<path
						d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"
					/>
				</svg>
			</a>
			<a
				href={DOWNLOAD_URL}
				class="rounded-md bg-[#111] px-5 py-2 text-sm font-semibold text-white hover:bg-[#333]"
			>
				Download
			</a>
		</div>
	</nav>
</header>

<!-- HERO -->
<section class="bg-white px-6 pt-14 pb-0 text-center">
	<div class="mx-auto max-w-3xl">
		<div
			class="mb-6 inline-block rounded-full border border-[#e5e5e5] px-4 py-1.5 text-xs font-medium tracking-widest text-[#737373] uppercase"
		>
			Free &amp; Open Source · macOS
		</div>

		<h1 class="mb-6 text-6xl leading-[1.05] font-black tracking-[-0.03em] text-[#111] sm:text-7xl">
			Change spaces,<br /> with a Blink.
		</h1>

		<p class="mx-auto mb-10 max-w-xl text-lg leading-relaxed text-[#737373]">
			Every macOS space switch wastes 0.5 seconds.<br />On ProMotion screens, a full second. Blink
			is the native fix.
		</p>

		<div class="flex flex-col items-center justify-center gap-3 sm:flex-row">
			<a
				href={DOWNLOAD_URL}
				class="inline-flex items-center gap-2 rounded-md bg-[#111] px-7 py-3.5 text-base font-semibold text-white hover:bg-[#333]"
			>
				<svg
					width="16"
					height="16"
					viewBox="0 0 24 24"
					fill="none"
					stroke="currentColor"
					stroke-width="2.5"
					stroke-linecap="round"
					stroke-linejoin="round"
				>
					<path d="M12 17V3M12 17l-5-5M12 17l5-5M3 21h18" />
				</svg>
				Download for Mac
			</a>
			<button
				onclick={copyBrew}
				class="inline-flex items-center gap-2 rounded-md border border-[#e5e5e5] bg-[#f5f5f5] px-5 py-3.5 font-mono text-sm text-[#111] hover:border-[#111] hover:bg-white"
			>
				<svg
					width="14"
					height="14"
					viewBox="0 0 24 24"
					fill="none"
					stroke="currentColor"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
					class="shrink-0 text-[#737373]"
				>
					{#if brewCopied}
						<polyline points="20 6 9 17 4 12" />
					{:else}
						<rect x="9" y="9" width="13" height="13" rx="2" ry="2" /><path
							d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"
						/>
					{/if}
				</svg>
				{BREW_COMMAND}
			</button>
		</div>
	</div>

	<!-- VIDEO COMPARISON -->
	<div class="mx-auto mt-16 max-w-6xl">
		<div class="overflow-hidden rounded-t-2xl bg-[#111]">
			<div class="grid grid-cols-1 sm:grid-cols-2">
				<!-- Before -->
				<div class="relative border-b border-[#2a2a2a] sm:border-r sm:border-b-0">
					<div class="flex items-center gap-2 border-b border-[#2a2a2a] px-5 py-3">
						<span class="h-2 w-2 rounded-full bg-[#ef4444]"></span>
						<span class="text-xs font-medium tracking-widest text-[#737373] uppercase"
							>Without Blink</span
						>
					</div>
					<video src="/videos/before.mp4" autoplay loop muted playsinline class="w-full"> </video>
				</div>
				<!-- After -->
				<div class="relative">
					<div class="flex items-center gap-2 border-b border-[#2a2a2a] px-5 py-3">
						<span class="h-2 w-2 rounded-full bg-[#22c55e]"></span>
						<span class="text-xs font-medium tracking-widest text-[#737373] uppercase"
							>With Blink</span
						>
					</div>
					<video src="/videos/after.mp4" autoplay loop muted playsinline class="w-full"> </video>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- STAT BAR -->
<section class="border-y border-[#e5e5e5] bg-[#f5f5f5]">
	<div class="mx-auto max-w-6xl px-6">
		<div
			class="grid grid-cols-1 divide-y divide-[#e5e5e5] sm:grid-cols-3 sm:divide-x sm:divide-y-0"
		>
			<div class="px-8 py-8 text-center">
				<div class="mb-1 text-4xl font-black tracking-tight text-[#111]">0.5s</div>
				<div class="text-sm text-[#737373]">wasted per space switch on macOS</div>
			</div>
			<div class="px-8 py-8 text-center">
				<div class="mb-1 text-4xl font-black tracking-tight text-[#111]">1.0s</div>
				<div class="text-sm text-[#737373]">on ProMotion (120 Hz) MacBook Pros</div>
			</div>
			<div class="px-8 py-8 text-center">
				<div class="mb-1 text-4xl font-black tracking-tight text-[#111]">&lt;10 MB</div>
				<div class="text-sm text-[#737373]">total app size</div>
			</div>
		</div>
	</div>
</section>

<!-- FEATURES -->
<section class="bg-white px-6 py-24">
	<div class="mx-auto max-w-6xl">
		<div class="mb-16">
			<h2 class="text-4xl font-black tracking-[-0.02em] text-[#111] sm:text-5xl">
				Everything you need.<br />Nothing you don't.
			</h2>
		</div>

		<div class="grid grid-cols-1 gap-px bg-[#e5e5e5] sm:grid-cols-2 lg:grid-cols-3">
			{#each features as feature}
				<div class="bg-white px-8 py-8">
					<h3 class="mb-2 text-lg font-bold text-[#111]">{feature.title}</h3>
					<p class="text-sm leading-relaxed text-[#737373]">{feature.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- WHY BLINK / COMPARISON -->
<section class="bg-[#111] px-6 py-24">
	<div class="mx-auto max-w-6xl">
		<div class="mb-4">
			<div class="mb-4 text-xs font-medium tracking-widest text-[#737373] uppercase">
				The alternatives
			</div>
			<h2 class="text-4xl font-black tracking-[-0.02em] text-white sm:text-5xl">
				Every other fix<br />has a tradeoff.
			</h2>
		</div>
		<p class="mb-16 max-w-xl text-[#737373]">
			Blink is the only solution that makes space switching instant without disabling system
			protections, abandoning native spaces, or paying for a bloated utility suite.
		</p>

		<div class="overflow-x-auto">
			<table class="w-full min-w-[560px] border-collapse">
				<thead>
					<tr class="border-b border-[#2a2a2a]">
						<th
							class="py-3 pr-8 text-left text-xs font-medium tracking-widest text-[#737373] uppercase"
							>App</th
						>
						{#each comparisonColumns as col}
							<th
								class="px-4 py-3 text-center text-xs font-medium tracking-widest text-[#737373] uppercase"
								>{col.label}</th
							>
						{/each}
					</tr>
				</thead>
				<tbody>
					{#each comparisonRows as row}
						<tr class="border-b border-[#2a2a2a] {row.highlight ? 'bg-white/5' : ''}">
							<td
								class="py-4 pr-8 pl-3 font-semibold {row.highlight
									? 'text-white'
									: 'text-[#737373]'}"
							>
								{row.name}
								{#if row.highlight}
									<span class="ml-2 rounded-sm bg-white px-1.5 py-0.5 text-xs font-bold text-[#111]"
										>You're here</span
									>
								{/if}
							</td>
							{#each comparisonColumns as col}
								<td class="px-4 py-4 text-center">
									{#if row.values[col.key]}
										<span class="text-white">✓</span>
									{:else}
										<span class="text-[#3a3a3a]">✗</span>
									{/if}
								</td>
							{/each}
						</tr>
					{/each}
				</tbody>
			</table>
		</div>
	</div>
</section>

<!-- INSTALL / CTA -->
<section class="bg-[#f5f5f5] px-6 py-24" id="download">
	<div class="mx-auto max-w-6xl">
		<div class="grid grid-cols-1 gap-16 lg:grid-cols-2">
			<div>
				<div class="mb-4 text-xs font-medium tracking-widest text-[#737373] uppercase">
					Get Blink
				</div>
				<h2 class="mb-4 text-5xl font-black tracking-[-0.02em] text-[#111]">
					Download.<br />Install. Done.
				</h2>
				<p class="mb-8 text-[#737373]">
					No account. No subscription. No catch. Blink is free and open source under the GPL-3.0
					License.
				</p>
				<a
					href={DOWNLOAD_URL}
					class="inline-flex items-center gap-2 rounded-md bg-[#111] px-8 py-4 text-base font-semibold text-white hover:bg-[#333]"
				>
					<svg
						width="16"
						height="16"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					>
						<path d="M12 17V3M12 17l-5-5M12 17l5-5M3 21h18" />
					</svg>
					Download .dmg
				</a>
			</div>

			<div class="flex flex-col gap-6">
				<div>
					<div class="mb-3 text-sm font-semibold text-[#111]">Install with Homebrew</div>
					<div class="flex items-center gap-3 rounded-md border border-[#e5e5e5] bg-white p-4">
						<code class="flex-1 font-mono text-sm text-[#111]">{BREW_COMMAND}</code>
						<button
							onclick={copyBrew}
							class="shrink-0 rounded border border-[#e5e5e5] px-3 py-1.5 text-xs font-medium text-[#737373] hover:border-[#111] hover:text-[#111]"
						>
							{brewCopied ? 'Copied' : 'Copy'}
						</button>
					</div>
				</div>

				<div>
					<div class="mb-3 text-sm font-semibold text-[#111]">Install manually</div>
					<p class="text-sm text-[#737373]">
						Download the <code class="rounded bg-white px-1.5 py-0.5 font-mono text-xs text-[#111]"
							>Blink.dmg</code
						>
						file using the Download button and drag Blink into your Applications folder.
					</p>
				</div>

				<div class="border-t border-[#e5e5e5] pt-6">
					<a
						href={GITHUB_URL}
						class="inline-flex items-center gap-2 text-sm text-[#737373] hover:text-[#111]"
					>
						<svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
							<path
								d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"
							/>
						</svg>
						View source on GitHub
					</a>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- FOOTER -->
<footer class="bg-[#111] px-6 py-12">
	<div class="mx-auto max-w-6xl">
		<div class="flex flex-col items-start justify-between gap-8 sm:flex-row sm:items-center">
			<div class="flex items-center gap-2.5">
				<img src="/icon.png" alt="Blink icon" class="h-7 w-7 rounded-[8px]" />
				<span class="text-base font-semibold text-white">Blink</span>
			</div>

			<div class="flex flex-wrap items-center gap-6">
				<a href={GITHUB_URL} class="text-sm text-[#737373] hover:text-white">GitHub</a>
				<a href="{GITHUB_URL}/blob/main/LICENSE" class="text-sm text-[#737373] hover:text-white"
					>GPL-3.0 License</a
				>
				<a href="{GITHUB_URL}/releases" class="text-sm text-[#737373] hover:text-white">Releases</a>
			</div>
		</div>

		<div class="mt-10 border-t border-[#2a2a2a] pt-8">
			<p class="text-xs text-[#3a3a3a]">
				Blink is not affiliated with Apple Inc. macOS is a trademark of Apple Inc.
			</p>
		</div>
	</div>
</footer>

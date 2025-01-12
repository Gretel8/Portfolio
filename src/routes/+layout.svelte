<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar, LightSwitch } from '@skeletonlabs/skeleton';

	// Highlight JS
	import hljs from 'highlight.js/lib/core';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs } from '@skeletonlabs/skeleton';
	import xml from 'highlight.js/lib/languages/xml'; // for HTML
	import css from 'highlight.js/lib/languages/css';
	import javascript from 'highlight.js/lib/languages/javascript';
	import typescript from 'highlight.js/lib/languages/typescript';
	import { initializeStores, Modal } from '@skeletonlabs/skeleton';

	initializeStores();

	hljs.registerLanguage('xml', xml);
	hljs.registerLanguage('css', css);
	hljs.registerLanguage('javascript', javascript);
	hljs.registerLanguage('typescript', typescript);
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar background="bg-base-500">
			<svelte:fragment slot="lead">
				<a href="/" class="text-sm text-center sm:text-xl hover:text-primary-500 ml-4"
					>Gretel Arcia</a
				>
			</svelte:fragment>

			<svelte:fragment slot="trail">
				<!-- About Me Link -->
				<a
					class="btn btn-sm variant-ghost-secondary hover:variant-ghost-primary flex iems-center"
					href="/#about"
				>
					<i class="material-icons inline md:hidden">person</i>
					<span class="hidden md:inline">About Me</span>
				</a>

				<!-- Experience Link -->
				<a
					class="btn btn-sm variant-ghost-secondary hover:variant-ghost-primary flex items-center"
					href="/#experience"
				>
					<i class="material-icons inline md:hidden">work</i>
					<span class="hidden md:inline">Experience</span>
				</a>

				<!-- Projects Link -->
				<a
					class="btn btn-sm variant-ghost-secondary hover:variant-ghost-primary flex items-center"
					href="/#projects"
				>
					<i class="material-icons inline md:hidden">code</i>
					<span class="hidden md:inline">Projects</span>
				</a>

				<!-- Contact Link -->
				<a
					class="btn btn-sm variant-ghost-secondary hover:variant-ghost-primary flex items-center"
					href="/#contact"
				>
					<i class="material-icons inline md:hidden">mail</i>
					<span class="hidden md:inline">Contact</span>
				</a>

				<!-- LightSwitch -->
				<LightSwitch class="hidden sm:flex" />
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>

	<!-- Page Route Content -->
	<slot />

	<!-- Footer -->
	<footer class="py-6">
		<div class="container mx-auto text-center">
			<div class="flex justify-center items-center space-x-4 mb-4">
				<!-- GitHub Link -->
				<a
					href="https://github.com/Gretel8"
					target="_blank"
					rel="noopener noreferrer"
					aria-label="GitHub"
					class="hover:text-primary-500"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="w-8 h-8"
						fill="currentColor"
						viewBox="0 0 24 24"
					>
						<path
							d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.205 11.385.6.11.82-.26.82-.577 0-.285-.01-1.04-.015-2.04-3.338.726-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.09-.744.083-.729.083-.729 1.205.084 1.84 1.237 1.84 1.237 1.07 1.835 2.807 1.305 3.492.998.107-.776.418-1.305.76-1.605-2.665-.305-5.466-1.332-5.466-5.93 0-1.31.467-2.38 1.235-3.22-.125-.305-.535-1.53.115-3.18 0 0 1.005-.322 3.3 1.23.955-.265 1.98-.397 3-.403 1.02.006 2.045.138 3 .403 2.28-1.552 3.285-1.23 3.285-1.23.655 1.65.245 2.875.12 3.18.77.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.43.37.815 1.096.815 2.21 0 1.595-.015 2.875-.015 3.27 0 .315.21.694.825.577C20.565 21.8 24 17.3 24 12c0-6.63-5.37-12-12-12z"
						/>
					</svg>
				</a>

				<!-- LinkedIn Link -->
				<a
					href="https://www.linkedin.com/in/gretel-arcia/"
					target="_blank"
					rel="noopener noreferrer"
					aria-label="LinkedIn"
					class="hover:text-primary-500"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="w-8 h-8"
						fill="currentColor"
						viewBox="0 0 24 24"
					>
						<path
							d="M20.451 20.451H17.54v-5.445c0-1.296-.026-2.966-1.805-2.966-1.806 0-2.082 1.41-2.082 2.868v5.543h-2.91V9.007h2.794v1.561h.039c.39-.738 1.341-1.513 2.762-1.513 2.954 0 3.498 1.943 3.498 4.469v6.927zM5.337 7.433c-.939 0-1.704-.763-1.704-1.705 0-.943.765-1.704 1.704-1.704.944 0 1.705.76 1.705 1.704s-.76 1.705-1.705 1.705zM6.782 20.451H3.891V9.007h2.891v11.444zM22.225 0H1.771C.792 0 0 .792 0 1.771v20.451C0 23.208.792 24 1.771 24h20.451C23.208 24 24 23.208 24 22.225V1.771C24 .792 23.208 0 22.225 0z"
						/>
					</svg>
				</a>
			</div>

			<p class="text-sm">
				Made by Gretel Arcia 🐼 &copy; {new Date().getFullYear()}. All Rights Reserved.
			</p>
		</div>
	</footer>
</AppShell>

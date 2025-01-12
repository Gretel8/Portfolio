<script lang="ts">
	import Carousel from './Carousel.svelte';
	export let title: string;
	export let screenshots: string[];
	export let overview: string;
	export let features: string;
	export let techStack: { src: string; alt: string; title: string }[];
	export let githubLink: string;
</script>

<div class="relative card p-4 sm:py-8 shadow-lg">
	<!-- Title-->
	<div class="flex items-center justify-center my-2">
		<h2 class="text-lg sm:text-2xl font-bold sm:text-left mb-2">{title}</h2>
	</div>

	<!-- Project Image -->
	<Carousel {screenshots} />

	<div class="mx-0 md:mx-12">
		<!-- Overview -->
		<p class="font-semibold text-sm sm:text-base">Overview:</p>
		<p class="text-sm sm:text-base">
			{overview}
		</p>

		<!-- Features -->
		<p class="mt-2 font-semibold text-sm sm:text-base">Features:</p>
		<p class="text-sm sm:text-base">{features}</p>

		<!-- Tech Stack -->
		<div class="flex mt-4 space-x-3">
			{#each techStack as tech}
				<img
					src={tech.src}
					alt={tech.alt}
					title={tech.title}
					class="h-6 max-w-8 sm:h-8 sm:max-w-10"
				/>
			{/each}
		</div>
		<p class="mt-4 text-right text-sm sm:text-base">
			<a
				href={githubLink}
				class="underline font-semibold hover:text-primary-500"
				target="_blank"
				rel="noopener noreferrer">View on GitHub</a
			>
		</p>
	</div>
</div>

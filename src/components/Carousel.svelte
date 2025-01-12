<script lang="ts">
	export let screenshots: string[]; // Array of screenshot URLs
	let elemCarousel: HTMLDivElement;

	function carouselLeft(): void {
		const x =
			elemCarousel.scrollLeft === 0
				? elemCarousel.clientWidth * elemCarousel.childElementCount // loop
				: elemCarousel.scrollLeft - elemCarousel.clientWidth; // step left
		elemCarousel.scroll(x, 0);
	}

	function carouselRight(): void {
		const x =
			elemCarousel.scrollLeft === elemCarousel.scrollWidth - elemCarousel.clientWidth
				? 0 // loop
				: elemCarousel.scrollLeft + elemCarousel.clientWidth; // step right
		elemCarousel.scroll(x, 0);
	}
</script>

<div class="grid py-4 grid-cols-[auto_1fr_auto] gap-1 items-center">
	<!-- Button: Left -->
	<button type="button" class="btn-icon" on:click={carouselLeft}>
		<i class="material-icons">chevron_left</i>
	</button>

	<!-- Carousel -->
	<div bind:this={elemCarousel} class="snap-x snap-mandatory scroll-smooth flex overflow-x-auto">
		{#each screenshots as screenshot}
			<img
				class="snap-center rounded-container-token"
				src={screenshot}
				alt="Project Screenshot"
				loading="lazy"
			/>
		{/each}
	</div>

	<!-- Button: Right -->
	<button type="button" class="btn-icon" on:click={carouselRight}>
		<i class="material-icons">chevron_right</i>
	</button>
</div>

<style>
</style>

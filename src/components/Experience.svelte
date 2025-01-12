<script lang="ts">
	export let logoLight = '';
	export let logoDark = '';
	export let title = '';
	export let employer = '';
	export let desktopDuration = '';
	export let mobileDuration = '';
	export let description = '';
	export let skills = [];
</script>

<div class="card p-4 sm:p-6 shadow-lg flex flex-col items-center gap-4 sm:flex-row sm:items-start">
	<!-- Light Mode Logo -->
	<img
		src={logoLight}
		alt={`${title} Logo Light`}
		class="w-20 p-2 self-center hidden sm:block dark:hidden"
	/>
	<!-- Dark Mode Logo -->
	<img
		src={logoDark}
		alt={`${title} Logo Dark`}
		class="w-20 p-2 self-center hidden sm:dark:block"
	/>
	<!-- Content -->
	<div>
		<!-- Mobile Header -->
		<div class="text-lg sm:hidden flex items-center gap-4">
			<img src={logoLight} alt={`${employer} Logo Light`} class="w-10 dark:hidden" />
			<img src={logoDark} alt={`${employer} Logo Dark`} class="w-10 hidden dark:block" />
			<div>
				<span class="block font-bold">{title}</span>
				<span class="text-primary-500 font-semibold">{employer}</span> • {mobileDuration}
			</div>
		</div>
		<!-- Desktop Header -->
		<h3 class="text-lg hidden sm:block sm:text-xl font-bold">
			{title} • <span class="text-primary-500">{employer}</span> • {desktopDuration}
		</h3>

		<p class="mt-2 text-sm sm:text-base">{description}</p>

		<!-- Skills -->
		<div class="flex mt-4 space-x-3">
			{#each skills as skill}
				<img
					src={skill.src}
					alt={skill.alt}
					title={skill.title}
					class="h-6 max-w-8 sm:h-8 sm:max-w-10"
				/>
			{/each}
		</div>
	</div>
</div>

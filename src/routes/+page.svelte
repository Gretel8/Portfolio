<script lang="ts">
	import Contact from '../components/Contact.svelte';
	import Experience from '../components/Experience.svelte';
	import Project from '../components/Project.svelte';

	// Calculate duration from start date to present
	function calculateDuration(startDate: Date): { desktop: string; mobile: string } {
		const now = new Date();
		const years = now.getFullYear() - startDate.getFullYear();
		const months = now.getMonth() - startDate.getMonth();

		const totalMonths = years * 12 + months;
		const displayYears = Math.floor(totalMonths / 12);
		const displayMonths = totalMonths % 12;

		let desktop = '';
		let mobile = '';

		if (displayYears > 0 && displayMonths > 0) {
			desktop = `${displayYears} year${displayYears > 1 ? 's' : ''}, ${displayMonths} month${displayMonths > 1 ? 's' : ''}`;
			mobile = `${displayYears}.${displayMonths} years`;
		} else if (displayYears > 0) {
			desktop = `${displayYears} year${displayYears > 1 ? 's' : ''}`;
			mobile = `${displayYears} year${displayYears > 1 ? 's' : ''}`;
		} else {
			desktop = `${displayMonths} month${displayMonths > 1 ? 's' : ''}`;
			mobile = `${displayMonths} mo${displayMonths > 1 ? 's' : ''}`;
		}

		return { desktop, mobile };
	}

	// Start date for current Software Engineer role
	const currentRoleStartDate = new Date(2025, 3); // April 2025 (month is 0-indexed)
	const currentDuration = calculateDuration(currentRoleStartDate);

	// Experience Data
	const experiences = [
		{
			logoLight: '/images/logos/ukg-logo.png',
			logoDark: '/images/logos/ukg-logo-dark.png',
			title: 'Software Engineer',
			employer: 'UKG',
			desktopDuration: currentDuration.desktop,
			mobileDuration: currentDuration.mobile,
			description: `Develop enterprise-scale onboarding applications used by millions of employees worldwide. Work with cross-functional Agile teams to deliver reliable, scalable systems that support critical onboarding experiences.`,
			skills: [
				{ src: '/images/logos/angular-logo.png', alt: 'Angular', title: 'Angular' },
				{ src: '/images/logos/typescript-logo.svg', alt: 'TypeScript', title: 'TypeScript' },
				{ src: '/images/logos/javascript-logo.jpg', alt: 'JavaScript', title: 'JavaScript' },
				{ src: '/images/logos/csharp-logo.png', alt: 'C#', title: 'C#' },
				{ src: '/images/logos/net-logo.png', alt: '.NET', title: '.NET' },
				{ src: '/images/logos/mongodb-logo.svg', alt: 'MongoDB', title: 'MongoDB' }
			]
		},
		{
			logoLight: '/images/logos/ukg-logo.png',
			logoDark: '/images/logos/ukg-logo-dark.png',
			title: 'Software Engineer Intern',
			employer: 'UKG',
			desktopDuration: '10 months',
			mobileDuration: '10 mos',
			description: `Contributed across multiple teams working on both web and mobile platforms. On the UKG Pro Benefits Hub team, built and enhanced user-facing Angular features, resolved UI defects, and improved reliability through automated regression testing. Later joined the UKG Pro Mobile App team as an iOS developer, helping deliver new features and performance improvements.`,
			skills: [
				{ src: '/images/logos/angular-logo.png', alt: 'Angular', title: 'Angular' },
				{ src: '/images/logos/typescript-logo.svg', alt: 'TypeScript', title: 'TypeScript' },
				{ src: '/images/logos/ngrx-logo.svg', alt: 'NgRx', title: 'NgRx' },
				{ src: '/images/logos/rxjs-logo.png', alt: 'RxJS', title: 'RxJS' },
				{ src: '/images/logos/sass-logo.png', alt: 'Sass', title: 'Sass' },
				{ src: '/images/logos/java-logo.png', alt: 'Java', title: 'Java' },
				{ src: '/images/logos/sql-logo.png', alt: 'SQL', title: 'SQL' },
				{ src: '/images/logos/nightwatch-logo.png', alt: 'Nightwatch', title: 'Nightwatch' },
				{ src: '/images/logos/swift-logo.png', alt: 'Swift', title: 'Swift' },
				{ src: '/images/logos/cordova_logo_normal.png', alt: 'Cordova', title: 'Cordova' },
				{ src: '/images/logos/appium-logo.png', alt: 'Appium', title: 'Appium' }
			]
		},
		{
			logoLight: '/images/logos/xymogen-logo.png',
			logoDark: '/images/logos/xymogen-logo.png',
			title: 'Stability Coordinator',
			employer: 'Xymogen',
			desktopDuration: '4 years, 7 months',
			mobileDuration: '4.6 years',
			description: `At Xymogen, I spearheaded the Stability Coordinator role, expanding the program by 180%. I
					analyzed product degradation trends to back shelf-life claims and ensure product quality.
					I also worked closely with the R&D team on supplement formulations, wrote detailed
					protocols, and supported lab investigations.`,
			skills: [
				{
					src: '/images/logos/office-logo.png',
					alt: 'Microsoft Office',
					title: 'Microsoft Office'
				},
				{ src: '/images/logos/six-sigma-logo.png', alt: 'Lean Six Sigma', title: 'Lean Six Sigma' }
			]
		},
		{
			logoLight: '/images/logos/dli-logo.png',
			logoDark: '/images/logos/dli-logo.png',
			title: 'Forensic Serologist',
			employer: 'DNA Labs International',
			desktopDuration: '2 years, 8 months',
			mobileDuration: '2.7 years',
			description: `At DLI, I conducted serological testing and microscopy to analyze evidence from crime
					scenes, including blood, body fluids, and hair. I performed DNA extraction,
					purification, and PCR amplification for the development of DNA profiles. I also
					collaborated with law enforcement on forensic casework and testified as an expert
					witness in DNA extraction.`,
			skills: [
				{
					src: '/images/logos/office-logo.png',
					alt: 'Microsoft Office',
					title: 'Microsoft Office'
				},
				{ src: '/images/logos/dna.png', alt: 'Forensic Biology', title: 'Forensic Biology' }
			]
		}
	];

	// Project Data
	const projects = [
		{
			title: 'CrimeLens LA',
			screenshots: [
				'/images/project-screenshots/crimelens-1.png',
				'/images/project-screenshots/crimelens-2.png',
				'/images/project-screenshots/crimelens-3.png',
				'/images/project-screenshots/crimelens-4.png'
			],
			overview:
				'A web application designed to analyze crime trends in Los Angeles over the past four years, providing law enforcement, researchers, and the public with interactive filters and visualizations to explore the data effectively.',
			features:
				'Full-stack development, interactive data visualizations, Oracle database integration, SQL query optimization',
			techStack: [
				{ src: '/images/logos/svelte-logo.svg', alt: 'Sveltekit', title: 'Sveltekit' },
				{ src: '/images/logos/oracle-logo.png', alt: 'Oracle', title: 'Oracle' },
				{ src: '/images/logos/sql-logo.png', alt: 'SQL', title: 'SQL' },
				{ src: '/images/logos/daisyui-logo.png', alt: 'Daisy UI', title: 'Daisy UI' },
				{ src: '/images/logos/chartjs-logo.png', alt: 'Chart.js', title: 'Chart.js' }
			],
			githubLink: 'https://github.com/Gretel8/CrimeLensLA'
		},
		{
			title: 'FoodBridge: Donation Platform',
			screenshots: [
				'/images/project-screenshots/foodbridge-1.png',
				'/images/project-screenshots/foodbridge-2.png',
				'/images/project-screenshots/foodbridge-3.png',
				'/images/project-screenshots/foodbridge-4.png'
			],
			overview:
				'A platform designed to connect food donors, such as grocery stores and individuals, with shelters in need. The app provides tailored user experiences for donors and shelters, enabling efficient coordination and reducing food waste.',
			features:
				'Firebase Authentication, donation form with food type selection and scheduling, dynamic dashboards for activity tracking, profile management, and donation history',
			techStack: [
				{ src: '/images/logos/angular-logo.png', alt: 'Angular', title: 'Angular' },
				{
					src: '/images/logos/firebase-auth-logo.png',
					alt: 'Firebase Auth',
					title: 'Firebase Auth'
				}
			],
			githubLink: 'https://github.com/Gretel8/FoodBridge2.0'
		}
	];
</script>

<!-- Landing Section -->
<section
	id="landing"
	class="h-screen flex flex-col justify-normal sm:justify-center items-center px-4"
>
	<div class="text-center flex flex-col pt-16 sm:pt-0 items-center">
		<div class="animate-typewriter block">
			<h1 class="h1 text-4xl sm:text-5xl md:text-7xl">Hi, I'm Gretel</h1>
		</div>
		<!-- Animated Logo -->
		<figure>
			<section class="img-bg" />
			<img
				src="/images/logos/profile-photo.jpg"
				alt="Profile Photo"
				class="h-40 sm:h-64 md:h-80 object-contain rounded-xl m-10"
			/>
		</figure>
		<div class="space-y-4 text-lg sm:text-xl mt-6 px-4">
			<p>A full-stack software engineer building scalable, user-focused applications.</p>
		</div>

		<!-- Down Arrow -->
		<a
			href="#about"
			id="scroll-arrow"
			class="hover:text-primary-500 mt-8 animate-bounce inline-block"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="w-8 h-8 sm:w-10 sm:h-10 hover:text-primary-500"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
			</svg>
		</a>
	</div>
</section>

<!-- About Section -->
<section id="about" class="flex flex-col justify-center items-center py-12 px-4 sm:py-16">
	<h1 class="h1 text-center text-3xl sm:text-4xl md:text-5xl mb-8">
		<span
			class="bg-gradient-to-br from-blue-500 to-cyan-300 bg-clip-text text-transparent box-decoration-clone"
		>
			About Me
		</span>
	</h1>
	<div class="card rounded-xl shadow-lg max-w-6xl bg-secondary px-4 py-6 sm:px-6 sm:py-8">
		<!-- Card Body -->
		<div class="p-4">
			<!-- Card Content -->
			<div class="space-y-6 text-base sm:text-lg">
				<section>
					<p>
						I started my professional journey in an unexpected place: forensic science. As a
						serologist at DNA Labs International, I performed critical forensic analyses and even
						stepped into the courtroom as an expert witness to help solve complex criminal cases —
						think CSI, minus the dramatic soundtrack. 
					</p>
					<p class="mt-4">
						Collaborating with software teams and laboratory systems over the years sparked my
						passion for technology. This led me to pursue a second bachelor's in Computer Science at
						the University of Florida, which I completed in May 2025.
					</p>
					<p class="mt-4">
						Today, I’m a Software Engineer at UKG, where I build scalable, enterprise-grade software
						used by millions around the world. I work across the full stack, developing
						dynamic web applications with Angular and TypeScript, building RESTful APIs, and
						creating backend services using C#, .NET, and MongoDB. I enjoy collaborating with
						cross-functional teams to turn complex problems into reliable, high-impact solutions.
					</p>
					<p class="mt-4">
						Outside of work, I love spending time outdoors, exploring new places, and planning my
						next travel adventure.
					</p>
					<p class="mt-4">
						I bring a unique blend of scientific rigor and technical expertise to everything I
						build, and I’m driven by the opportunity to create software that makes everyday life a
						little brighter.
					</p>
				</section>
			</div>
		</div>
	</div>
</section>

<!-- Experience Section -->
<section id="experience" class="py-12 px-4 sm:py-16">
	<h1 class="h1 text-center text-3xl sm:text-4xl md:text-5xl mb-8">
		<span
			class="bg-gradient-to-br from-red-500 to-yellow-500 bg-clip-text text-transparent box-decoration-clone"
		>
			Experience
		</span>
	</h1>
	<div class="container mx-auto space-y-8 max-w-6xl">
		{#each experiences as exp}
			<Experience
				logoLight={exp.logoLight}
				logoDark={exp.logoDark}
				title={exp.title}
				employer={exp.employer}
				desktopDuration={exp.desktopDuration}
				mobileDuration={exp.mobileDuration}
				description={exp.description}
				skills={exp.skills}
			/>
		{/each}
	</div>
	<div class="flex justify-center">
		<a class="btn btn-md variant-filled-primary mt-8" href="/resume">View Résumé </a>
	</div>
</section>

<!-- Projects Section -->
<section id="projects" class="py-12 sm:py-16">
	<h1 class="h1 text-center pb-8">
		<span
			class="bg-gradient-to-br from-pink-500 to-violet-500 bg-clip-text text-transparent box-decoration-clone"
		>
			Projects
		</span>
	</h1>
	<div class="mx-4 sm:mx-8">
		<div class="container mx-auto max-w-6xl space-y-8">
			{#each projects as project}
				<Project
					title={project.title}
					screenshots={project.screenshots}
					overview={project.overview}
					features={project.features}
					techStack={project.techStack}
					githubLink={project.githubLink}
				/>
			{/each}
		</div>
	</div>
</section>

<!-- Contact Section -->
<section id="contact" class="py-12 sm:py-16">
	<h1 class="h1 text-center pb-8">
		<span
			class="bg-gradient-to-br from-green-500 to-blue-500 bg-clip-text text-transparent box-decoration-clone"
		>
			Contact
		</span>
	</h1>
	<Contact />
</section>

<style lang="postcss">
	figure {
		@apply flex relative flex-col;
	}
	figure svg,
	.img-bg {
		@apply w-64 h-64 md:w-80 md:h-80;
		margin-left: 60px;
	}
	.img-bg {
		@apply absolute z-[-1] rounded-full blur-[50px] transition-all;
		animation:
			pulse 5s cubic-bezier(0, 0, 0, 0.5) infinite,
			glow 5s linear infinite;
	}
	@keyframes glow {
		0% {
			@apply bg-primary-400/50;
		}
		33% {
			@apply bg-secondary-400/50;
		}
		66% {
			@apply bg-tertiary-400/50;
		}
		100% {
			@apply bg-primary-400/50;
		}
	}
	@keyframes pulse {
		50% {
			transform: scale(1.5);
		}
	}

	.animate-typewriter h1 {
		margin: 0 auto;
		overflow: hidden;
		border-right: 3px solid rgba(236, 73, 230, 0.75);
		white-space: nowrap;
		animation:
			typing 1.5s steps(15) forwards,
			blink 0.6s steps(15, end) infinite;
	}

	@keyframes typing {
		from {
			width: 0;
		}
		to {
			width: 100%;
		}
	}
	@keyframes blink {
		from {
			border-right-color: rgba(236, 73, 230, 0.75);
		}
		50% {
			border-right-color: transparent;
		}
	}

	#scroll-arrow {
		display: flex;
		justify-content: center;
		align-items: center;
		color: var(--color-primary);
		transition: color 0.3s ease-in-out;
	}

	#scroll-arrow:hover {
		color: var(--color-accent);
		cursor: pointer;
	}

	@keyframes bounce {
		0%,
		100% {
			transform: translateY(0);
		}
		50% {
			transform: translateY(-10px);
		}
	}

	.animate-bounce {
		animation: bounce 2s infinite;
	}

	.badge {
		@apply bg-primary-500 text-white rounded-md px-2 py-1 text-sm;
	}

	.card img {
		@apply rounded-t-lg;
	}
</style>

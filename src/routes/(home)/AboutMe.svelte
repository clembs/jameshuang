<script lang="ts">
	import Chip from '$lib/components/Chip.svelte';
	import Status from '$lib/components/Status.svelte';
	import { onMount } from 'svelte';
	import { page } from '$app/stores';
	import ScrollToButton from './ScrollToButton.svelte';

	const skills = [
		'UI & UX',
		'Web',
		'Print',
		'Motion',
		'Social Media',
		'Branding',
		'Figma',
		'Framer',
		'After Effects'
	];

	let sectionEl: HTMLElement;
	let sectionAnimationPercent = 0;

	// the more you scroll down, the more the opacity increases and the more the section moves up
	function animateSection() {
		const sectionRect = sectionEl.getBoundingClientRect();

		sectionAnimationPercent = Math.max(
			(window.innerHeight - (sectionRect.top - sectionRect.height / 2)) / window.innerHeight,
			0
		);
	}

	onMount(animateSection);
</script>

<svelte:window on:scroll={animateSection} />

<section
	bind:this={sectionEl}
	id="about-me"
	style="opacity: {sectionAnimationPercent};
	transform: translateY(calc(-20px * {sectionAnimationPercent}))
"
>
	<section id="intro">
		<h2>
			Hi, my name is <br />
			<span class="highlighted">James Huang</span>.
		</h2>
		<p>
			I'm James - a designer, artist, and endlessly curious person who enjoys creating things that are both thoughtful and visually compelling.
<br />
			<br />
			I'm interested in the intersection of design, technology, and art, and spend my time working on projects through my youth-run design agency, Magnificent, or exploring new artistic practices like painting and photography. I enjoy moving between disciplines rather than staying within the boundaries of one.
 <br />
			<br />
			Currently, I'm an 18-year-old high school student based in Sydney. When I'm not studying, you'll probably find me reading something new, watching a movies with friends, wandering through galleries or national parks, exploring the city with my camera.
<br />
			<br />
		</p>
	</section>

	<section id="info">
		<section id="skills">
			<h2>Skills</h2>

			<div id="chips">
				{#each skills as skill}
					<Chip>{skill}</Chip>
				{/each}
			</div>
		</section>

		<section id="status">
			<h2>Status</h2>

			<ul>
				{#each $page.data.status as status}
					<li class="status">
						<Status {status} />
					</li>
				{/each}
			</ul>
		</section>
	</section>
</section>

<ScrollToButton href="#projects">
	Scroll down to see <b>my work</b>
</ScrollToButton>

<style lang="scss">
	#about-me {
		display: flex;
		gap: 5rem;
		max-width: 900px;
		width: 95%;
		margin: 0 auto;
		padding: 3rem var(--space-lg);
		opacity: 0;

		section {
			display: flex;
			flex-direction: column;
			gap: 0.5rem;
			// min-width: 350px;
		}

		#intro {
			width: 100%;

			h2 {
				font-size: var(--font-size-xl);
			}

			p {
				text-align: justify;
			}
		}

		#info {
			gap: 2rem;
		}

		#chips {
			display: flex;
			gap: 0.75rem;
			flex-wrap: wrap;
		}

		#status ul {
			display: flex;
			flex-direction: column;
			gap: 1rem;
			padding: 0;
			list-style: none;
		}

		@media (max-width: 1020px) {
			flex-direction: column;
			gap: 1rem;

			#intro h2 br {
				display: none;
			}

			#status ul {
				flex-direction: row;

				li {
					width: 100%;
				}
			}
		}

		@media (max-width: 800px) {
			#status ul {
				flex-direction: column;
			}

			#intro h2 br {
				display: block;
			}
		}
	}
</style>

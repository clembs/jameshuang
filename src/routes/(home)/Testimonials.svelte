<script lang="ts">
	import { onMount } from 'svelte';
	import Testimonial from './Testimonial.svelte';

	let sectionEl: HTMLElement;
	let sectionAnimationPercent = 0;

	// the more you scroll down, the more the opacity increases and the more the section moves up
	function animateSection() {
		const sectionRect = sectionEl.getBoundingClientRect();

		sectionAnimationPercent = Math.max(
			(window.innerHeight - (sectionRect.top - sectionRect.height / 1.5)) / window.innerHeight,
			0
		);
	}

	onMount(animateSection);
</script>

<svelte:window on:scroll={animateSection} />

<section
	bind:this={sectionEl}
	id="testimonials-section"
	style="opacity: {sectionAnimationPercent};
  transform: translateY(calc(-50px * {sectionAnimationPercent}));"
>
	<ul id="testimonials">
		<Testimonial
			quote={`<span class="highlight">Incredible output, organised, diligent, proactive...</span>
			I'm privileged to have him on our Team at Catalyst Chemistry.`}
			profile={{
				name: 'Jeff Tse',
				avatarUrl: '/testimonials/avatars/jeff-tse.png',
				position: 'Founder @ Catalyst Chemistry',
				brandLogoUrl: '/testimonials/logos/catalyst-chemistry.svg',
				brandName: 'Catalyst Chemistry'
			}}
		/>
		<Testimonial
			quote={`James is great to work with. He's <span class="highlight">dedicated</span> to his craft...
			and produces <span class="highlight">great quality UX/UI</span> output.`}
			profile={{
				name: 'Daniel Radovich',
				avatarUrl: '/testimonials/avatars/daniel-radovich.png',
				position: 'Director, Lead Product Designer @ Raw Studio',
				brandLogoUrl: '/testimonials/logos/raw.svg',
				brandName: 'Raw Studio'
			}}
		/>
		<Testimonial
			quote={`James is one of the few designers I know that makes you think
					<span class="highlight">'why would I want it any other way?'.</span>`}
			profile={{
				name: 'Darren Candra',
				avatarUrl: '/testimonials/avatars/darren-candra.png',
				position: 'Founder @ Subjective Labs',
				brandLogoUrl: '/testimonials/logos/subjective-labs.png',
				brandName: 'Subjective Labs'
			}}
		/>
	</ul>
</section>

<style lang="scss">
	#testimonials-section {
		padding: var(--space-xxl) var(--space-xxl);
		margin: 0 auto;
		max-width: 1400px;

		@media (max-width: 600px) {
			padding: var(--space-md) var(--space-sm);
		}
	}

	#testimonials {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: var(--space-lg);
		list-style: none;
		padding: 0;
		margin: 0 auto;
	}
</style>

<script lang="ts">
	export let quote: string;
	export let profile: {
		name: string;
		position: string;
		avatarUrl: string;
		brandName: string;
		brandLogoUrl: string;
	};
</script>

<li class="testimonial-wrapper">
	<div class="testimonial-border">
		<div class="testimonial">
			<div class="quote">
				{@html quote}
			</div>
			<div class="author">
				<div class="profile">
					<img
						draggable="false"
						src={profile.avatarUrl}
						alt={profile.name}
						height="40"
						width="40"
						class="avatar"
					/>
					<div class="text">
						<div class="name">{profile.name}</div>
						<p class="position">{profile.position}</p>
					</div>
				</div>
				<img
					draggable="false"
					src={profile.brandLogoUrl}
					alt="{profile.brandName}'s logo"
					class="logo"
				/>
			</div>
		</div>
	</div>

	<!-- Quote icon -->
	<svg
		class="quote-icon"
		width="35"
		height="28"
		viewBox="0 0 35 28"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
	>
		<path
			d="M5.34242 17.1328C6.16667 15.9141 7.50606 14.8984 9.77273 14.8984C13.1727 14.8984 15.8515 17.5391 15.8515 21.0938C15.8515 25.3594 12.5545 28 8.53636 28C4.62121 28 0.5 25.0547 0.5 18.5547C0.5 10.6328 5.65152 3.45313 12.7606 0L13.3788 3.11719C7.19697 6.67188 4.10606 10.0234 4.10606 14.2891C4.10606 15.7109 4.62121 16.7266 5.34242 17.1328ZM23.9909 17.1328C24.8152 15.9141 26.1545 14.8984 28.4212 14.8984C31.8212 14.8984 34.5 17.5391 34.5 21.0938C34.5 25.3594 31.203 28 27.1848 28C23.2697 28 19.1485 25.0547 19.1485 18.5547C19.1485 10.6328 24.3 3.45313 31.4091 0L32.0273 3.11719C25.8455 6.67188 22.7545 10.0234 22.7545 14.2891C22.7545 15.7109 23.2697 16.7266 23.9909 17.1328Z"
			fill="url(#paint0_linear_1624_3344)"
		/>
		<defs>
			<linearGradient
				id="paint0_linear_1624_3344"
				x1="17.5"
				y1="2"
				x2="17.5"
				y2="28"
				gradientUnits="userSpaceOnUse"
			>
				<stop stop-color="white" />
				<stop offset="1" stop-color="white" stop-opacity="0.2" />
			</linearGradient>
		</defs>
	</svg>
</li>

<style lang="scss">
	.testimonial-wrapper {
		position: relative;
		height: fit-content;
	}

	.quote-icon {
		position: absolute;
		top: -28px;
		left: 50%;
		transform: translate(-50%, 50%);
	}

	.testimonial-border {
		--space-from-center: 35px;
		--border-size: 1px;

		padding: var(--border-size);
		background-image: linear-gradient(
			180deg,
			var(--color-foreground-lowest),
			var(--color-foreground-lowerest)
		);
		border-radius: calc(var(--space-lg) + var(--border-size));
		height: fit-content;
		clip-path: polygon(
			0 0,
			0 100%,
			100% 100%,
			100% 0,
			calc(50% + var(--space-from-center)) 0,
			calc(50% + var(--space-from-center)) var(--border-size),
			calc(50% - var(--space-from-center)) var(--border-size),
			calc(50% - var(--space-from-center)) 0
		);
	}

	.testimonial {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: var(--space-lg);
		padding: var(--space-xl);
		border-radius: var(--space-lg);
		background-color: var(--color-background);

		.quote {
			font-size: var(--font-size-md);
			color: var(--color-foreground-low);

			:global(.highlight) {
				color: var(--color-foreground-full);
			}
		}

		.author {
			display: flex;
			justify-content: space-between;
			gap: var(--space-md);
			align-items: center;
			width: 100%;
			padding-left: var(--space-md);
			border-left: 2px solid var(--color-foreground-low);

			.profile {
				display: grid;
				grid-template-columns: auto 1fr;
				gap: var(--space-md);
				align-items: center;

				.avatar {
					border-radius: 50%;
					background-color: var(--color-foreground-low);
					font-size: 0px;
				}

				.name {
					font-weight: 500;
					color: var(--color-foreground-full);
				}

				.position {
					font-size: var(--font-size-sm);
					text-wrap: balance;
					opacity: 0.75;
				}
			}

			.logo {
				width: auto;
				height: 30px;
				max-width: 45px;
			}
		}
	}
</style>

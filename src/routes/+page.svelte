<script>
	import Button from '../shared/button.svelte';
	import Slider from '../shared/slider.svelte';
	import Toggle from '../shared/toggle.svelte';
</script>

<!-- ---  -->

<header>
	<h1>Simple, traffic-based pricing</h1>
	<p>
		Sign-up for our 30-day trial.
		<br />
		No credit card required.
	</p>
</header>

<main>
	<p>100k Pageviews</p>

	<div class="slider-conteiner">
		<Slider />
	</div>

	<p class="price"><span class="bold">$16.00</span> /month</p>

	<div class="toggle-container">
		<p>Monthly Billing</p>
		<Toggle />
		<p>
			Yearly Billing <span class="discount">25%</span>
		</p>
	</div>

	<hr />

	<ul>
		<li>Unlimited websites</li>
		<li>100% data ownership</li>
		<li>Email reports</li>
	</ul>

	<Button>Start my trial</Button>
</main>

<!-- ---  -->
<style>
	@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@600;800&display=swap');

	:root {
		/* Primary */
		--clr-Soft-Cyan: hsl(174, 77%, 80%); /* (Full Slider Bar) */
		--clr-Strong-Cyan: hsl(174, 86%, 45%); /* (Slider Backround) */
		--clr-Light-Grayish-Red: hsl(14, 92%, 95%); /* (Discount Background) */
		--clr-Light-Red: hsl(15, 100%, 70%); /* (Discount Text) */
		--clr-Pale-Blue: hsl(226, 100%, 87%); /* (CTA Text) */
		/* Neutral */
		--clr-White: hsl(0, 0%, 100%); /* (Pricing Component Background) */
		--clr-Very-Pale-Blue: hsl(230, 100%, 99%); /* (Main Background) */
		--clr-Light-Grayish-Blue: hsl(224, 65%, 95%); /* (Empty Slider Bar) */
		--clr-Light-Grayish-Blue: hsl(223, 50%, 87%); /* (Toggle Background) */
		--clr-Grayish-Blue: hsl(225, 20%, 60%); /* (Text) */
		--clr-Dark-Desaturated-Blue: hsl(227, 35%, 25%); /* (Text & CTA Background) */
	}

	* {
		box-sizing: border-box;
	}

	:global(body) {
		margin: 0;
		padding: 0;

		min-height: 100vh;
		max-width: 100vw;

		font-family: 'Manrope', sans-serif;
		font-size: 15px;
		font-weight: 600;
		text-align: center;

		background-color: var(--clr-Pale-Blue);
	}

	h1,
	.bold {
		color: var(--clr-Dark-Desaturated-Blue);
		font-size: 2.5rem;
		font-weight: 800;
	}

	p,
	li {
		color: var(--clr-Grayish-Blue);
		font-size: 0.8em;
	}

	/* Main styles  */

	:global(body) {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 5vh;
	}

	header,
	main {
		width: 90%;
	}

	header {
		background-image: url('/pattern-circles.svg');
		background-repeat: no-repeat;
		background-position: center;
		background-size: contain;
	}
	header h1 {
		font-size: 1.2em;
	}

	main {
		padding: 1rem;
		border-radius: 1rem;
		background-color: var(--clr-White);

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	main > p:first-of-type {
		text-transform: uppercase;
		letter-spacing: 0.1rem;
	}

	main hr {
		border: none;
		border-bottom: 1px solid var(--clr-Light-Grayish-Blue);
	}

	ul {
		padding: 0;
		list-style-type: none;
	}
	li::before {
		content: url('/icon-check.svg');
		margin-right: 0.5rem;
	}

	.price {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 0.5rem;
	}

	.discount {
		padding: 0.1rem 0.5rem;

		border-radius: 1rem;

		color: var(--clr-Light-Red);
		background-color: var(--clr-Light-Grayish-Red);
	}
	.discount::before {
		content: '-';
	}

	.toggle-container {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 0.3rem;
	}

	.slider-conteiner {
		width: 80%;
		margin: 1rem 0;
	}

	@media (min-width: 768px) {
		.discount::before {
			content: '';
		}
		.discount::after {
			content: ' discount';
		}
	}
</style>

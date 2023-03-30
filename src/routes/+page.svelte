<script>
	import Button from '../shared/button.svelte';
	import Slider from '../shared/slider.svelte';
	import Toggle from '../shared/toggle.svelte';

	let price = [
		{ pageviews: '10K', perMonth: 8 },
		{ pageviews: '50K', perMonth: 12 },
		{ pageviews: '100K', perMonth: 16 },
		{ pageviews: '500K', perMonth: 24 },
		{ pageviews: '1M', perMonth: 36 }
	];

	let sliderValue = 0;
	let toggleValue = false;
	let finalPrice;

	$: {
		finalPrice = price[sliderValue].perMonth;

		if (toggleValue) {
			finalPrice = (finalPrice * 3) / 4;
		}
	}
</script>

<!-- ---  -->

<header>
	<h1>Simple, traffic-based pricing</h1>
	<p>
		Sign-up for our 30-day trial.
		<br class="mobile" />
		No credit card required.
	</p>
</header>

<main>
	<div class="top-section">
		<p class="split">{price[sliderValue].pageviews} Pageviews</p>

		<div class="slider-conteiner">
			<Slider min="0" max="4" on:valueChange={(event) => (sliderValue = event.detail.value)} />
		</div>

		<p class="price"><span class="bold">${finalPrice}.00</span> /month</p>
	</div>

	<div class="toggle-container">
		<p>Monthly Billing</p>
		<Toggle on:valueChange={(event) => (toggleValue = event.detail.checked)} />
		<p>
			Yearly Billing <span class="discount">25%</span>
		</p>
	</div>

	<div class="separator">
		<ul>
			<li>Unlimited websites</li>
			<li>100% data ownership</li>
			<li>Email reports</li>
		</ul>

		<Button>Start my trial</Button>
	</div>
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
		--clr-Very-Pale-Blue: hsl(230, 86%, 95%); /* (Main Background) */
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

		background-color: var(--clr-Very-Pale-Blue);
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

	.split {
		text-transform: uppercase;
		letter-spacing: 0.1rem;
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
		max-width: 30rem;
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

	.top-section {
		width: 100%;
	}

	.separator {
		margin-top: 1rem;
		padding: 0.5rem;

		width: 100%;
		border-top: 1px solid rgba(211, 211, 211, 0.5);
	}

	ul {
		padding: 0;
		list-style-type: none;
		line-height: 2;
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
		width: 90%;
		margin: 1rem auto;
	}

	@media (min-width: 768px) {
		header h1 {
			font-size: 1.8em;
		}

		.discount::before {
			content: '';
		}
		.discount::after {
			content: ' discount';
		}

		.top-section {
			display: grid;
			grid-template-columns: repeat(2, minmax(0, 1fr));
			align-items: center;
			gap: 1rem;
		}
		.slider-conteiner {
			grid-column: 1 / 3;
			grid-row: 2 / 2;
		}

		.separator {
			display: flex;
			justify-content: space-evenly;
			align-items: center;
		}

		.toggle-container {
			gap: 0.8rem;
		}

		ul {
			text-align: left;
		}

		.mobile {
			display: none;
		}
	}
</style>

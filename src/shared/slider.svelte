<script>
	export let max = 100;
	export let min = 1;
	export let value = 50;

	$: filled = Math.floor((value / (max - min)) * 100);
</script>

<!-- ---  -->

<div class="container" style="--filled-precent: {filled}%;">
	<input type="range" name="cost-slider" class="slider" bind:value {min} {max} />
</div>

<!-- ---  -->
<style>
	.container {
		margin: 0;
		padding: 0;
		position: relative;

		--slider-height: 1rem;
		--thumb-size: 2.2rem;
	}

	.slider {
		appearance: none;

		width: 100%;
		height: var(--slider-height);

		background-color: transparent;
	}

	.slider::-webkit-slider-runnable-track {
		height: 0.5rem;

		border-radius: 2rem;

		background: linear-gradient(
			to right,
			var(--clr-Soft-Cyan) var(--filled-precent),
			var(--clr-Light-Grayish-Blue) var(--filled-precent)
		);

		cursor: pointer;
	}

	.slider::-webkit-slider-thumb {
		appearance: none;

		width: var(--thumb-size);
		height: var(--thumb-size);

		border-radius: 100%;

		transform: translate(0, -40%);

		background-color: var(--clr-Strong-Cyan);
		box-shadow: 0px 0px 10px var(--clr-Strong-Cyan);

		background-image: url('/icon-slider.svg');
		background-repeat: no-repeat;
		background-position: center;

		--bgi-size: 1.5em;
		background-size: var(--bgi-size) calc(var(--bgi-size) / 2);
	}

	.slider::-webkit-slider-thumb:hover {
		opacity: 0.85;
	}

	.slider::-webkit-slider-thumb:active {
		background-color: hsl(174, 83%, 29%);
	}
</style>

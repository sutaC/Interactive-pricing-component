<script>
	export let checked = false;
</script>

<input type="checkbox" name="toggle" id="toggle" bind:checked />
<label for="toggle" class="toggle-button" />

<style>
	input {
		display: none;
	}

	.toggle-button {
		position: relative;
		width: 2.6rem;
		height: 1.4rem;
		border-radius: 1rem;

		background-color: var(--clr-Light-Grayish-Blue);

		cursor: pointer;
	}
	.toggle-button::after {
		content: '';
		position: absolute;

		top: 50%;
		left: 30%;

		transform: translate(-50%, -50%);

		width: 1rem;
		height: 1rem;
		border-radius: 100%;
		background-color: white;
	}
	input:checked + .toggle-button {
		background-color: var(--clr-Strong-Cyan);
	}
	input:checked + .toggle-button::after {
		left: 70%;
	}
</style>

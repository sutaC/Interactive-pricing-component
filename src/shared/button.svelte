<button on:click><slot /></button>

<style>
	button {
		padding: 0.75rem 2.5rem;

		border: none;
		border-radius: 2rem;

		background-color: var(--clr-Dark-Desaturated-Blue);
		color: var(--clr-Pale-Blue);
	}

	button:active {
		color: white;
	}
</style>

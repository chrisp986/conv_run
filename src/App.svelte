<script>
	let minPerMile = 8; // Initial value
	let minPerKm = convertMinPerMileToKm(minPerMile);

	function convertMinPerMileToKm(minutesPerMile) {
		return (minutesPerMile / 1.609).toFixed(2);
	}

	function convertMinPerKmToMile(minutesPerKm) {
		return (minutesPerKm * 1.609).toFixed(2);
	}

	function handleMinPerKmChange(event) {
		minPerKm = parseFloat(event.target.value);
		minPerMile = convertMinPerKmToMile(minPerKm);
	}

	function handleMinPerMileChange(event) {
		minPerMile = parseFloat(event.target.value);
		minPerKm = convertMinPerMileToKm(minPerMile);
	}
</script>

<div class="container">
	<form>
		<label for="minPerMile">Minutes per Mile:</label>
		<div class="rotating-menu">
			<select
				id="minPerMile"
				bind:value={minPerMile}
				on:change={handleMinPerMileChange}
			>
				{#each Array(281)
					.fill(0)
					.map((_, i) => (i / 20 + 1).toFixed(2)) as value}
					<option {value}>{value}</option>
				{/each}
			</select>
		</div>
		<input
			type="number"
			id="minPerMileNumber"
			step="0.05"
			bind:value={minPerMile}
			on:input={handleMinPerMileChange}
		/>
	</form>

	<form>
		<label for="minPerKm">Minutes per Kilometer:</label>
		<div class="rotating-menu">
			<select
				id="minPerKm"
				bind:value={minPerKm}
				on:change={handleMinPerKmChange}
			>
				{#each Array(281)
					.fill(0)
					.map((_, i) => (i / 20 + 0.62).toFixed(2)) as value}
					<option {value}>{value}</option>
				{/each}
			</select>
		</div>
		<input
			type="number"
			id="minPerKmNumber"
			step="0.05"
			bind:value={minPerKm}
			on:input={handleMinPerKmChange}
		/>
	</form>
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 1rem;
	}

	form {
		display: flex;
		flex-direction: column;
		margin-bottom: 1rem;
		width: 100%;
		max-width: 400px;
	}

	label {
		margin-bottom: 0.5rem;
	}

	input,
	select,
	button {
		margin-bottom: 1rem;
		padding: 0.5rem;
		font-size: 1rem;
		width: 100%;
	}

	.rotating-menu {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.rotating-menu select {
		font-size: 1rem;
	}

	@media (min-width: 600px) {
		.container {
			flex-direction: row;
			justify-content: space-around;
		}

		form {
			width: 45%;
		}
	}
</style>

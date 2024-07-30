<script>
	let minPerMile = 8; // Initial value for the slider
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
		<input
			type="range"
			id="minPerMile"
			min="1"
			max="15"
			step="0.05"
			bind:value={minPerMile}
			on:input={handleMinPerMileChange}
			class="slider"
		/>
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
		<input
			type="number"
			id="minPerKm"
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
	button,
	.slider {
		margin-bottom: 1rem;
		padding: 0.5rem;
		font-size: 1rem;
		width: 100%;
	}

	.slider {
		-webkit-appearance: none;
		appearance: none;
		height: 10px;
		background: #ddd;
		outline: none;
		opacity: 0.7;
		transition: opacity 0.2s;
	}

	.slider:hover {
		opacity: 1;
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

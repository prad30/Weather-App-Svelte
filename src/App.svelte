<script>
	import Searchbar from "./components/Searchbar.svelte";
	import Weatherdata from "./components/Weatherdata.svelte";

	let weatherData;

	const weatherDataFetch = async (city) => {
		try {
			const response = await fetch(
				`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${process.env.API_KEY}`,
			);

			console.log(response);
			
			const data = await response.json();
			
			console.log(data);

			weatherData = {
				city: data.name,
				temperature:Math.floor(data.main.temp)-273,
			};
		} catch (error) {
			alert("Enter a Valid City");            
		}
	};
</script>

<main>
	<Searchbar on:search={(e) => weatherDataFetch(e.detail)} />
	{#if weatherData}
		<Weatherdata {weatherData} />
	{:else}
		<p class="message">Enter a City and Press Enter</p>
	{/if}
</main>

<style>
	.message {
		font-size: 30px;
	}
</style>

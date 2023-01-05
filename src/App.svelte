<script>
  import Tile from './tile.svelte'
  const getWeather = (async () => {
    const WEATHER_API_KEY = "ff2d84fa4fb1438bb9b41129223112"
    const url = ' http://api.weatherapi.com/v1/forecast.json?' + new URLSearchParams({key:WEATHER_API_KEY, q:"Taipei"})
    console.log(url)
    const weather = await fetch(url, {mode:'cors'})
    return await weather.json()
    })()

</script>

{#await getWeather}
  <p>...waiting</p>
{:then data}
  <h1>The weather in {data.location.name} is...</h1>
  <p>{data.current.condition.text}</p>
  <Tile windDegree={data.current.wind_degree} conditionText={data.current.condition.text} windSpeed={data.current.wind_kph} conditionIcon={data.current.condition.icon} temp={data.current.temp_c} windDirection={data.current.wind_dir}/>
 
{:catch error}
  <p>Some error occured</p>
{/await}


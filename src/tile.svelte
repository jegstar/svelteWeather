<script>
  export let conditionText;
  export let conditionIcon;
  export let temp;
  export let windSpeed;
  export let windDegree;
  export let windDirection;
</script>

<style>
  img {
    height:100px;
  }
  div {
    display:grid;
    grid-template:1fr 1fr 1fr / 1fr 1fr 1fr;
    gap: 1em;
    border:2px solid red;
  }
</style> 

<div>
  <img src={conditionIcon} alt={conditionText} />
  <h1>{temp}</h1>
  <img src='arrow.png' alt='{windDirection}' style="transform:rotate({windDegree}deg)" />
  <p>{conditionText}</p>
  <p>&#176;C</p>
  <p>{windSpeed}kph</p>

</div>

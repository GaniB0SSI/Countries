<script>
  import { onMount } from "svelte";
  let countries = [];

  onMount(async () => {
    const res = await fetch("https://restcountries.com/v3.1/all");
    countries = await res.json();
  });
</script>

<h1>Countries</h1>
<ul>
  {#each countries as country}
    <li>
      <a href={"/countries/" + country.cca3}>{country.name.common}</a>
    </li>
  {/each}
</ul>

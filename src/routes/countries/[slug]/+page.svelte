<script>
  import { onMount } from "svelte";
  import { page } from "$app/stores";

  let country;
  let slug = $page.params.slug;
  onMount(async () => {
    const res = await fetch(`https://restcountries.com/v3.1/alpha/${slug}`);
    const data = await res.json();
    if (data.length > 0) {
      country = data[0];
    }
  });
</script>

{#if country}
  <h1>{country.name.common}</h1>
  <p><strong>Capital:</strong> {country.capital ? country.capital[0] : "N/A"}</p>
  <p><strong>Region:</strong> {country.region}</p>
  <p><strong>Population:</strong> {country.population.toLocaleString()}</p>
  <img src={country.flags.svg} alt="Flag" width="200" />
{:else}
{/if}

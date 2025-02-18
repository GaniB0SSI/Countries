<script>
    import { onMount } from "svelte";
    let countries = [];
  
    onMount(async () => {
      const res = await fetch("https://restcountries.com/v3.1/all");
      countries = await res.json();
    });
  </script>
  
  <h1>Countries of the world</h1>
  <ul>
    {#each countries as country}
      <li>
        <a href={"/countries/" + country.cca3}>{country.name.common}</a>
      </li>
    {/each}
  </ul>
  
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      color: rgb(66, 185, 240);
      font-family: 'Arial', sans-serif;
      padding: 20px;
    }
  
    h1 {
      text-align: center;
      font-size: 2.5rem;
      margin-bottom: 20px;
      font-weight: 600;
      color: #1f95e4;
    }
  
    ul {
      list-style-type: none;
      padding-left: 0;
    }
  
    li {
      margin: 10px 0;
    }
  
    a {
      color: #1815b9;
      text-decoration: none;
      font-size: 1.2rem;
    }
  
    a:hover {
      color: #051725;
    }
  
    li:hover {
      background-color: #61a8eb;
    }

  </style>
  
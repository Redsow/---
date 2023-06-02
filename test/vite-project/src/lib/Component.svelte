<script>
    import { onMount } from 'svelte';

let data = {};



onMount(async () => {
  try {
    const response = await fetch(`https://newsapi.org/v2/everything?domains=wsj.com&apiKey=a3bfbc120b2349b78a775666333a10e0`);
    data = await response.json();
  } catch (error) {
    console.error('Ошибка при получении данных:', error);
  }
});
  </script>
  
  <div>
    {#if Object.keys(data).length > 0}
      <h2>{data.title}</h2>
      <p>{data.description}</p>
    {:else}
      <p>Загрузка данных...</p>
    {/if}
  </div>
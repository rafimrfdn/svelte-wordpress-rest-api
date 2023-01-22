<script>
  import { onMount } from 'svelte';
  
  let posts = [];

  onMount(async () => {
    const res = await fetch('https://example.com/wp-json/wp/v2/posts');
    posts = await res.json();
  });
</script>

<h1>Fetch API Wordpress using SVELTE</h1>

<p>Here is the list articles: </p>
<ul>
  {#each posts as post}
    <li>{post.title.rendered}</li>
  {/each}
</ul>


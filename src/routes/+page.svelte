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

 <main class="container">
  {#each posts as post}
    <article>
      <header>
      <h3><a href="{post.link}">{post.title.rendered}</a></h3>

      <img src="{post.jetpack_featured_media_url}" alt="{post.title.rendered}"/>
              </header>

      {post.excerpt.rendered}

    </article>
  {/each}

 </main>

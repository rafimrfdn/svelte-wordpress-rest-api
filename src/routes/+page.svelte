<script>
  import { onMount } from "svelte";

  let posts = [];

  onMount(async () => {
    const res = await fetch("https://example.com/wp-json/wp/v2/posts");
    posts = await res.json();
  });
</script>

<main class="container">
  <h1>Fetch API Wordpress using SVELTE</h1>

  <p>Here is the list articles:</p>

  {#each posts as post}
    <article>
      <header>
        <h3><a href={post.link}>{post.title.rendered}</a></h3>

        <img src={post.jetpack_featured_media_url} alt={post.title.rendered} />
      </header>

      {@html post.excerpt.rendered}
      <footer>
        <small>Diposting pada : <b>{post.date}</b></small>
      </footer>
    </article>
  {/each}
</main>

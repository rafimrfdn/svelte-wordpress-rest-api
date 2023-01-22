<script>
  import { onMount } from "svelte";

  let title = "";
  let content = "";
  let status = "publish";
  let response = "";

  const createPost = async () => {
    const data = {
      title: title,
      content: content,
      status: status,
    };

    const res = await fetch("https://example.com/wp-json/wp/v2/posts", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: "Bearer YOUR_JWT_TOKEN",
      },
      body: JSON.stringify(data),
    });

    response = await res.json();
  };
</script>

<div class="container">
  <p>Silahkan isi artikel baru anda</p>
  <form on:submit|preventDefault={createPost}>
    <label>
      Title:
      <input type="text" bind:value={title} />
    </label>
    <br />
    <label>
      Content:
      <textarea bind:value={content} />
    </label>
    <br />
    <button type="submit">Create Post</button>
  </form>
</div>

<p>{response.message}</p>

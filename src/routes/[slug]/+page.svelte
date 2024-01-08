<script>
    export let data;
  </script>
  
  <svelte:head>
    <title>{data.blogPost.title}</title>
  </svelte:head>
  
  <main>
    {#if data.blogPost}
        <h1>{data.blogPost.title}</h1>
        <p>{@html data.blogPost.content.html}</p>
    {:else}
      <p>Post not found.</p>
    {/if}
  </main>
<script context="module">
  export const load = async ({ fetch }) => {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    const posts = await res.json();
    return {
      props: {
        posts,
      },
    };
  };
</script>

<script>
  export let posts;
</script>

<h1>Posts</h1>

<div class="posts">
  {#each posts as item}
    <div class="post">
      <h2>{item.title}</h2>
      <p>{item.body}</p>
      <p class="links"><a sveltekit:prefetch href={`/blogs/${item.id}`} > Read More </a></p>
    </div>
  {/each}
</div>

<style>
  .posts {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }

  .post {
    padding: 20px;
    border: 1px solid #ddd;
    box-shadow: 0 0 10px #eee;
  }
  h2 {
    margin: 0;
  }
  .links {
    text-align: right;
  }
</style>

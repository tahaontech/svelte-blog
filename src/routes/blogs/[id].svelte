<script context="module">
    export const load = async ({params, fetch}) => {
        const id = params.id
        const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);
        const post = await res.json()
        return {
            props: {
                post
            }
        }
    }
</script>

<script>
    export let post;
</script>

<h1>{post.title}</h1>
<p>{post.body}</p>
<script>
    import { fade } from "svelte/transition";

    let { title = $bindable(), body = $bindable(), image = $bindable(), showPaper } = $props();
</script>

<div in:fade={{ delay: 2000 }}>
    <label for="paperTitle">Title</label>
    <input name="paperTitle" bind:value={title} />
    <label for="paperBody">Body</label>
    <textarea name="paperBody" bind:value={body}></textarea>
    <label for="paperImage">Image URL</label>
    <input name="paperImage" bind:value={image} />
    <button onclick={() => showPaper()}>show</button>
</div>

<style>
    div {
        position: absolute;
        top: 0px;
        width: 400px;
        left: 0px;
        right: 0px;
        margin: 50px auto;
        display: flex;
        flex-direction: column;
    }

    input,
    textarea,
    button {
        font-family: "Inter", sans-serif;
        font-optical-sizing: auto;
        font-weight: 400;
        border-radius: 5px;
        border: 1px solid #555555;
    }

    input,
    textarea {
        padding: 10px;
    }

    label {
        font-family: "Inter", sans-serif;
        font-optical-sizing: auto;
        font-weight: 400;
        margin: 20px 0 10px;
    }

    textarea {
        height: 200px;
    }

    button {
        margin: 20px 0;
        padding: 10px;
    }
</style>

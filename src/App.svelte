<svelte:options customElement="animated-paper" />

<script lang="ts">
    import Form from "./lib/Form.svelte";
    import Paper from "./lib/Paper.svelte";

    let paperVisible = $state(false);

    let title = $state("title");
    let body = $state(
        "<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. </p><p>Duis accumsan at diam nec semper. Nullam feugiat eros ante, at hendrerit ligula cursus non. Nunc feugiat, antehendrerit luctus scelerisque, libero magna consectetur urna, id consequat purus risunec sapien. Cras euismod elit in nisl dignissim elementum. </p>"
    );
    let image = $state(
        "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Williams_FW06.jpg/1280px-Williams_FW06.jpg"
    );
</script>

<div class="paperContainer">
    {#if paperVisible}
        <Paper {title} {body} {image} hidePaper={() => (paperVisible = false)} />
    {:else}
        <Form bind:title bind:body bind:image showPaper={() => (paperVisible = true)} />
    {/if}
</div>

<style>
    .paperContainer {
        display: grid;
        grid-template-columns: 1;
        grid-auto-rows: 100%;
        width: 100%;
        height: 100%;
        overflow: hidden;
        justify-content: center;
        align-items: center;
    }
    /*   .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  } */
</style>

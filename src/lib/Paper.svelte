<script lang="ts">
    import { fade, fly } from "svelte/transition";
    import { cubicIn, quartOut } from "svelte/easing";
    import { onMount } from "svelte";

    let { title, body, image, hidePaper } = $props();

    let showLine = $state(false);

    onMount(() => {
        setTimeout(() => {
            showLine = true;
        }, 1000);
    });
</script>

<div
    class="paper"
    in:fly={{ x: -2000, duration: 1800, easing: quartOut }}
    out:fly={{ x: 2000, duration: 2000, easing: cubicIn }}
>
    <div class="paperHeading">
        <h1 in:fade={{ delay: 1000, duration: 2000 }}>{title}</h1>
        <div class={["paperLine", showLine ? "show" : ""]}></div>
    </div>
    <div class="paperParagraph" in:fade={{ delay: 2200, duration: 2000 }}>
        {@html body}
    </div>
    <div
        class="paperImage"
        in:fade={{ delay: 3000, duration: 2000 }}
        style:background-image={`url(${image})`}
    ></div>
    <div class="paperClose">
        <!-- svelte-ignore a11y_consider_explicit_label -->
        <button onclick={() => hidePaper()}>
            <svg
                xmlns="http://www.w3.org/2000/svg"
                height="40px"
                viewBox="0 -960 960 960"
                width="40px"
                fill="#1f1f1f"
                ><path
                    d="m251.33-204.67-46.66-46.66L433.33-480 204.67-708.67l46.66-46.66L480-526.67l228.67-228.66 46.66 46.66L526.67-480l228.66 228.67-46.66 46.66L480-433.33 251.33-204.67Z"
                /></svg
            >
        </button>
    </div>
</div>

<style>
    .paper {
        place-self: center center;
        max-width: 80%;
        max-height: 80%;

        display: grid;
        padding: 6%;

        aspect-ratio: 16 / 9;
        grid-template-columns: 50% 50%;
        grid-template-rows: 20% 80%;
        background-image: url("/paper.png");
        background-size: 100% 100%;
    }

    :global(.paperParagraph p) {
        grid-column-start: 1;
        font-family: "Inter", sans-serif;
        font-optical-sizing: auto;
        font-weight: 400;
        font-style: normal;
    }

    .paperParagraph {
        overflow-y: auto;
        scrollbar-color: #5d5b59 rgba(0, 0, 0, 0);
        scrollbar-width: thin;
        grid-column-start: 1;
        padding-right: 1em;
        line-height: 1.8em;
    }

    .paperImage {
        margin-left: 10%;
        height: 80%;
        width: 80%;
        background-size: cover;
        background-position: center;
        mask-image: url("/mask.png");
        mask-mode: luminance;
        mask-size: 100% 100%;
    }

    .paperLine {
        width: 70%;
        aspect-ratio: 10/ 1;
        background-image: url("/line.png");
        background-repeat: no-repeat;
        background-size: contain;
        mask-image: linear-gradient(#fff, #fff);
        mask-mode: luminance;
        mask-size: 0% 100%;
        mask-repeat: no-repeat;
        transition: all 3s;
        opacity: 0%;
    }

    .paperLine.show {
        mask-size: 100% 100%;
        opacity: 60%;
    }

    .paperClose {
        grid-column-start: 2;
        grid-row-start: 1;
        justify-self: end;
    }

    h1 {
        font-weight: 600;
        font-family: "Crimson Text", serif;
        font-style: normal;
        font-weight: 600;
        margin: 0;
        margin-bottom: 10px;
    }

    button {
        background: none;
        color: inherit;
        border: none;
        padding: 0;
        font: inherit;
        cursor: pointer;
        outline: inherit;
    }
</style>

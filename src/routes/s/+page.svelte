<script lang="ts">
    import { onMount } from "svelte";
    import "@fontsource/source-sans-pro";
        import "@fontsource/iosevka";
    let mode:string
    let text:string    
    let params = ""
    let customel:HTMLElement = document.createElement("link")
        customel.setAttribute("rel", "stylesheet")

    
    let cont = new URLSearchParams(window.location.search)
        mode = cont.get("m") || "basic"
        text = cont.get("t") || btoa(encodeURIComponent("Hello, world!"))
        text = decodeURIComponent(atob(text))

    if(mode == "basi") {
        customel.setAttribute("href", "/themes/basi.css")
    }

    if(mode == "mini") {
        customel.setAttribute("href", "/themes/mini.css")
    }

    if(mode == "term") {
        customel.setAttribute("href", "/themes/term.css")
    }
    if(mode == "dter") {
        customel.setAttribute("href", "/themes/dter.css")
    }

    if(mode == "grad") {
        customel.setAttribute("href", "/themes/colr.css")
    }

    if(mode == "colr") {
        customel.setAttribute("href", "/themes/onec.css")
    }

    if(mode == "ubun") {
        customel.setAttribute("href", "/themes/colr2.css")
    }
</script>
<div>{@html customel.outerHTML}</div>
<main>
    {#if mode == "basi"}
        {text}
    {:else if mode == "term" || mode == "dter"}
        <div class="selects">
            <div></div> <div></div> <div></div>
        </div>
        {text}
    {:else if mode == "grad" || mode == "mini" || mode == "colr" || mode == "ubun"}
        {text}
    {/if}
</main>

<style>
main {
    font-family: "source sans pro";
}
</style>
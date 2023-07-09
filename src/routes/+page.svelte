<script lang="ts">
    import "@fontsource/source-sans-pro"
	import { onMount } from "svelte";
    let outputtext:string = ""
    let inputtext:string  = ""
    let mode:string       = "basi"
    let url:string
    let els = {}
    function compile () {
        outputtext = "http://"+url+`/s?m=${(encodeURIComponent(mode))}&t=`+ btoa(encodeURIComponent(inputtext))
    }

    function setmode(newone:string) {
        //@ts-ignore
        els[newone] ||= undefined
        //@ts-ignore
        return (ev) => {
            mode = newone

            Object.values(els).forEach((el) => {
                //@ts-ignore
                el.classList.remove("focus")
            })

            ev.target.classList.add("focus")

        }
    }

    let ism = (mod:string) => {
        return mod == mode ? "focus" : ""
    }

    onMount(()=>{
     url = window.location.host
    })
</script>

<main>
    <section class="main">
        <div class="center1">
            <div class="title">EDLinkMe 2</div>
        </div>
        <div class="inputy output">
            <div class="center3">
                {outputtext}
            </div>
        </div>
        <div class="inputy">
            <div class="center2">
                <input type="text" placeholder="Napiš něco" class="input el" bind:value={inputtext}>
                <button class="el" on:click={compile}>OK</button>
            </div>
            <div class="center3 selections">
                <button class="selection focus" on:click={setmode("basi")} bind:this={els["basi"]}>Basic</button>
                <button class="selection" on:click={setmode("term")} bind:this={els["term"]}>Terminal</button>
                <button class="selection" on:click={setmode("dter")} bind:this={els["dter"]}>Dark terminal</button>
                <button class="selection" on:click={setmode("grad")} bind:this={els["grad"]}>Gradient</button>
                <button class="selection" on:click={setmode("mini")} bind:this={els["mini"]}>Minimal</button>
                <button class="selection" on:click={setmode("colr")} bind:this={els["colr"]}>One color</button>

                <button class="selection" on:click={setmode("ubun")} bind:this={els["ubun"]}>Ubuntu</button>
            </div>
        </div>
    </section>
    <section class="second">
        Made with <span class="orange">SvelteKIT</span> by <span class="red">MiftikCZ</span>.
    </section>
</main>

<style>
    :root {
        font-size: 20px;
    }
    * {
        box-sizing: border-box;
    }
    main {
        height: 100%;
        background: #eff1f5;
        color: #4c4f69;
        flex-direction: column;
        display: flex;
        font-family: "Source Sans Pro", sans-serif;
    }
    .second {
        min-height: 50vh;
        padding: 12px;
        color: #eff1f5;
        background: #51576d;
    }
    .main {
        min-height: 100vh;
        padding: 12px;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        display: flex;
        width: 100%;
        gap: 2em;
    }

    .main .center1 {
        letter-spacing: 3px;
        padding: 0.75em 0;
        font-size: 2.5em;
        widows: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .selections {
        letter-spacing: 3px;
        /* background: #ccd0da; */
        padding: 1em;
        gap: 2px;
        font-size: 1em;
        display: flex;
        flex-direction: column;
    }

    .selections .selection {
        padding: 0.25em 0.5em;
        text-align: start;
        font-size: 1em;
        border: none;
        width: 100%;
        color: #5c5f77;
        background: #9ca0b0;
        border-left: #0008 4px solid;
    }

    .selections .focus {
        background: #8839ef40;
        color: #4c4f69;
        border-left: #8839efe5 4px solid;
    }

    .inputy {
        width: 100%;
        max-width: 600px;
    }

    .main .inputy .center2 {
        gap: 0.25em;
        letter-spacing: 3px;
        padding: 0.75em 0;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .main .inputy .center3 {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .main .inputy .center2 .input{
        width: 100%;
        background: #eff1f5 !important;
        border: none;
        border: #9ca0b040 1px solid;
        box-shadow: #bcc0ccaa 0 8px 10px !important;
    } 

    .main .inputy .center2 .el {
        font-size: 1em;
        /* background: #bcc0cc; */
        border: none;
        border-radius: 0.25em;
        padding: 0.25em;
        /* border: #9ca0b040 1px solid;
        box-shadow: #bcc0cc 0 0 2px; */


        background: #eff1f5 !important;
        border: none;
        border: #9ca0b088 1px solid;
        box-shadow: #bcc0ccaa 0 8px 10px !important;
    }

    .main .inputy .center2 button{
        flex-shrink: 0;
        padding: .25em 0.75em !important;
    } 

    .output {
        word-wrap: break-word;
        word-break: break-all;
        width: 100%;
        padding: 0.75em;
        border: #9ca0b0 1px solid;
        background: #ccd0da;
        box-shadow: #ccd0da 0 0 2px;
        box-shadow: #bcc0cc88 0 0px 10px !important;
    }

    .orange {
        color: #ef9f76;
    }

    .red {
        color: #e78284;
    }
</style>
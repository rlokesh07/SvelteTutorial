<script lang="ts">
	import { receive } from "./transitions";
	import { getTwemojiUrl } from "./utils";



    export let found: string[];

</script>

<div class = "found">

    {#each found as emoji (emoji)}

        <div class="pair">
            <img in:receive={{key: `${emoji}:a`}} alt = {emoji} src = {getTwemojiUrl(emoji)}/>
            <img in:receive={{key: `${emoji}:b`}} alt = {emoji} src = {getTwemojiUrl(emoji)}/>
        </div>


    {/each}

</div>

<style>

    .found{

        display: flex;
        justify-content: center;
        align-items: center;
        gap: 4em;
        height: 100%;
        filter: drop-shadow(0.2em 0.2em 0.5em rgba(0,0,0,0.2));


    }
    
    .pair{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 4em;
        height: 4em;
        padding: 1em;
        border-radius: 50%;
    }

    img{   
        position:absolute;

        height: 2em;
        width: 2em;
    }
</style>
<script lang="ts">
	import { getTwemojiUrl } from "./utils";
	import {send} from "./transitions";

	export let emoji: string;

	export let selected: boolean;

	export let found: boolean;

	export let group: 'a' | 'b';
</script>

<div class="square" class:flipped={selected || found}>
	<button on:click />

	<div class="background">

	</div>


	{#if !found}
		<img out:send={ {key: `${emoji}:${group}`}}
		alt = {emoji} src={getTwemojiUrl(emoji)} />
	{/if}
</div>

<style>
	.square {
		display: flex;

		justify-content: center;
		align-items: center;
		transform-style: preserve-3d;
		transition: transform 0.4s;
	}
	.background{
		background: white;
		border: 0.5em solid #eee;
		transform: rotateY(180deg);
		backface-visibility: hidden;
		width: 100%;
		height: 100%;
		position: absolute;
		border-radius: 1em;
	}

	.flipped {

		transform: rotateY(180deg);
	}

	img {
		width: 6em;
		height: 6em;
		pointer-events: none;
		transform: rotateY(180deg);
		backface-visibility: hidden;
	}

	button {
		position: absolute;
		width: 100%;
		height: 100%;
		backface-visibility: hidden;
		background: #eee;
		border: 0;
		border-radius: 1em;
		font-size: inherit;

	}
	
</style>

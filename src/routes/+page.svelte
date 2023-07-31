<script lang="ts">
    import Stats from './Stats.svelte';
	import Fullscreen from './Fullscreen.svelte';
	import Dimensions from './Dimensions.svelte';
    import Keyboard from './Keyboard.svelte';
	let virtualKeyboardActive = false;

	if (typeof navigator !== 'undefined' && 'virtualKeyboard' in navigator) {
	    // The VirtualKeyboard API is supported!
        (navigator as any).virtualKeyboard.addEventListener('visibilitychange', () => {
            virtualKeyboardActive = (navigator as any).virtualKeyboard.visible;
        });

	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	{#if virtualKeyboardActive === false}	
	<div class="row">
		<h1>
			Welcome to the webapi demo for the Steam Deck
		</h1>
		<Stats />
	</div>
	{/if}
	<div class="row keyboard-tester">
		<input type="text" placeholder="bring up virtual keyboard..." />
		<Fullscreen />
	</div>
	<div class="row">
		<Dimensions />
		<Keyboard />
	</div>
</section>

<style>
	.row { 
		display: flex;
		flex-direction: row;
	}
	@media (max-width: 600px) {
		.row {
			flex-direction: column;
		}
	}
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}
	section > div {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}
	h1 {
		width: 100%;
	}
	.keyboard-tester {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.keyboard-tester input {
		border-radius: 5px;
		padding: 5px;
		border-color: var(--accent);
		cursor: pointer;
		margin-right: 5px;
	}
	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>

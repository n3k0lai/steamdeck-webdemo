<script lang="ts">
	let fullscreenActive = false;

	const toggleFullscreen = () => {
        if(typeof document !== 'undefined') {
            if (!fullscreenActive) {
                document.documentElement.requestFullscreen();
            } else {
                document.exitFullscreen();
            }
            fullscreenActive = !fullscreenActive;
        }
	};

	if(typeof document !== 'undefined') {
		fullscreenActive = document.fullscreen;
	};
</script>

<div class="fullscreen">
    <div on:click={toggleFullscreen}
         class:active={toggleFullscreen}>
         fullscreen: <span>{fullscreenActive ? 'ACTIVE' : 'OFF'}</span>
    </div>
</div>

<style>
	.fullscreen {
		display: flex;
	}
    .fullscreen div {
        background-color: var(--bg-dark);
        padding: 5px;
        border-radius: 5px;
        color: var(--bg-light);
        cursor: pointer;
    }
    .fullscreen div span {
        font-weight: bold;
        color: var(--accent);
    }
</style>

<script lang="ts">

	let virtualKeyboardDetected = false;
	let virtualKeyboardActive = false;
    let virtualKeyboardHeight = 0;
    let virtualKeyboardWidth = 0;
    let virtualKeyboardX = 0;
    let virtualKeyboardY = 0;

	if (typeof navigator !== 'undefined' && 'virtualKeyboard' in navigator) {
	    // The VirtualKeyboard API is supported!
	    virtualKeyboardDetected = true;

        virtualKeyboardHeight = (navigator as any).virtualKeyboard.height;
        virtualKeyboardWidth = (navigator as any).virtualKeyboard.width;
        virtualKeyboardX = (navigator as any).virtualKeyboard.x;
        virtualKeyboardY = (navigator as any).virtualKeyboard.y;

        (navigator as any).virtualKeyboard.addEventListener('resize', () => {
            virtualKeyboardHeight = (navigator as any).virtualKeyboard.height;
            virtualKeyboardWidth = (navigator as any).virtualKeyboard.width;
            virtualKeyboardX = (navigator as any).virtualKeyboard.x;
            virtualKeyboardY = (navigator as any).virtualKeyboard.y;
        });
        (navigator as any).virtualKeyboard.addEventListener('visibilitychange', () => {
            virtualKeyboardActive = (navigator as any).virtualKeyboard.visible;
        });

	}

</script>

<div class="keyboard">
    {#if virtualKeyboardActive}
	<div class="keyboard-widget"
         style:height={virtualKeyboardY}
         style:width={virtualKeyboardX}>
        <div class="keyboard-widget__tooltip left">
            width: <strong>{virtualKeyboardWidth}</strong>
        </div>
        <div class="keyboard-widget__tooltip top">
            height: <strong>{virtualKeyboardHeight}</strong>
        </div>
	</div>
    {/if}
	<div>
		virtual keyboard API detected: <strong>{virtualKeyboardDetected ? 'yes' : 'no'}</strong>
	</div>
	<div>
		virtual keyboard active: <strong>{virtualKeyboardActive ? 'yes' : 'no'}</strong>
	</div>
</div>

<style>
	.keyboard {
		display: flex;
		flex-direction: column;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}

    .keyboard-widget {
        background-color: var(--accent);
        border-radius: 0.5rem;
        margin: 1rem 0;
    }

    .keyboard-widget__tooltip {
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        font-size: 12px;
        padding: 0.5rem;
        border-radius: 0.5rem;
        color: var(--bg-light);
    }

    .keyboard-widget__tooltip.left {
        left: 0;
    }


    .keyboard-widget__tooltip.top {
        top: 0;
    }
</style>

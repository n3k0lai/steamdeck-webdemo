<script lang="ts">
    let windowWidth = 0;
    let windowHeight = 0;
    let windowOrientation = 'unknown';
    let widgetHeight = '0px';
    let widgetWidth = '0px';
    if(typeof window !== 'undefined') {
        windowWidth = window.innerWidth;
        windowHeight = window.innerHeight;
        windowOrientation = window.screen.orientation.type;
        widgetHeight = Math.round(window.innerHeight / 10) + 'px';
        widgetWidth = Math.round(window.innerWidth / 10) + 'px';
        // respond to window resize
        window.addEventListener('resize', () => {
            windowWidth = window.innerWidth;
            windowHeight = window.innerHeight;
            windowOrientation = window.screen.orientation.type;
            widgetHeight = Math.round(window.innerHeight / 10) + 'px';
            widgetWidth = Math.round(window.innerWidth / 10) + 'px';
        });
    }
</script>

<div class="dimensions">
    <div class="dimensions-widget" style:width={widgetWidth} style:height={widgetHeight}>
        <div class="dimensions-widget__tooltip left">
            width: <strong>{windowWidth}</strong>
        </div>
        <div class="dimensions-widget__tooltip top">
            height: <strong>{windowHeight}</strong>
        </div>
    </div>
    <div class="dimensions-widget__orientation">
        orientation: <strong>{windowOrientation}</strong>
    </div>
</div>

<style>
	.dimensions {
        position: relative;
		display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        margin-top: 20px;
	}

    .dimensions-widget {
        background-color: var(--accent);
        border-radius: 0.5rem;
        margin: 1rem 0;
    }
    .dimensions-widget__tooltip {
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        font-size: 12px;
        padding: 0.5rem;
        border-radius: 0.5rem;
        background-color: var(--bg-dark);
        opacity: 1;
        transition: opacity 0.2s ease-in-out;
        color: var(--bg-light);
    }
    .dimensions-widget__tooltip strong {
        color: var(--accent);
        margin-left: 0.5rem;
    }
    .dimensions-widget__tooltip.left {
        right: 90%;
        top: 50%;
        transform: translateY(-50%);
    }
    
    .dimensions-widget__tooltip.top {
        top: -20px;
        left: 0;
    }

    .dimensions-widget__orientation {
        display: flex;
        flex-direction: column;
    }
</style>

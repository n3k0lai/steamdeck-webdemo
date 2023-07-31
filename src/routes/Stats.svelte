<script lang="ts">

	let browser = 'browser undetected';
	let platform = 'platfom undetected';
	let locale = 'locale undetected';

	if(typeof navigator !== 'undefined') {
		browser = navigator.userAgent;
		platform = navigator.platform;
		locale = navigator.language;
	}
</script>

<div class="stats">
	<div>
		browser: <strong>{browser}</strong>
	</div>
	<div>
		pc: <strong>{platform}</strong>
	</div>
	<div>
		locale: <strong>{locale}</strong>
	</div>
</div>

<style>
	.stats {
		display: flex;
		flex-direction: column;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}

</style>

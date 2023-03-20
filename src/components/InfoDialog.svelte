<script lang="ts">
	import Button from "smelte/src/components/Button";

	import FancyDialog from "../common/FancyDialog.svelte";

	export let showDialog = true;
</script>

<FancyDialog small bind:showDialog>
	<h5 slot="title">D.S.I.W.D. (days since international women's day)</h5>

	<p>
		International women's day is important. Equally important is knowing
		exactly how many days since or hence you are from it.
	</p>

	<p>With DSIWD you can!</p>

	<div slot="actions">
		<Button text on:click={() => (showDialog = false)}>Wow, so cool!</Button
		>
		<Button text on:click={() => (showDialog = false)}>I love it!</Button>
	</div>
</FancyDialog>

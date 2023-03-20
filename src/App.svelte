<script lang="ts">
	import { onMount } from "svelte";
	onMount(() => {
		// force-reset scroll top, since for some reason browsers remember this
		document.body.scrollTop = 0;
	});

	import GithubCorner from "./common/GithubCorner.svelte";
	import Toast from "./common/Toast.svelte";

	function get_days_since_iwd() {
		let now = new Date();
		let year = now.getFullYear();
		let month = 2;
		let day = 8;
		let international_women_day = new Date(year, month, day);
		console.log(international_women_day);
		let delta = now.getTime() - international_women_day.getTime();

		if (delta < 0) {
			international_women_day = new Date(year - 1, month, day);
			delta = now.getTime() - international_women_day.getTime();
		}

		return Math.floor(delta / (1000 * 3600 * 24));
	}

	let days = get_days_since_iwd();
</script>

<main>
	<GithubCorner
		href="https://github.com/loremdipso/DSIWD"
		position="topRight"
		small
	/>

	<Toast />

	<div class="fade-in w-full fancy">
		<div>
			It's been<br /><span class="days">{days} days</span><br />since
			international women's day
		</div>
	</div>
</main>

<style lang="scss">
	.fancy {
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		color: white;
		text-align: center;
		font-size: 3rem;
		.days {
			font-weight: bold;
		}
	}

	:global(.actions-bar) {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		background-color: blue;
	}

	:global(html) {
		height: 100vh;
		overflow: hidden;
	}

	:global(body) {
		height: 100%;
		overflow-y: scroll;
		overflow-x: auto;
		background-color: black;
	}

	:global(a) {
		// TODO: figure out why this doesn't work
		// @apply text-blue-200;
		color: rgba(29, 142, 241, 1);
	}

	.slide-in-from-top {
		animation: 300ms cubic-bezier(0.17, 0.04, 0.03, 0.94) 0s 1 SlideDown;
	}
	@keyframes SlideDown {
		0% {
			transform: translate3d(0, -100%, 0);
		}
		100% {
			transform: translateZ(0);
		}
	}

	.fade-in {
		animation: 1s ease-out 0s 1 FadeIn;
	}
	@keyframes FadeIn {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	.icon {
		height: 30px;
		display: inline;
	}
</style>

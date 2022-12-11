<script>
	import { page } from '$app/stores';
	import { fade } from 'svelte/transition';
	import '../app.css';
	import MainAnimation from '../lib/MainAnimation.svelte';
	import Menu from '../lib/Menu.svelte';
	import Transition from '../lib/Transition.svelte';

	let shouldShowName = true;
	let shouldShowPage = false;

	setTimeout(() => {
		shouldShowName = true;
	}, 1000);
	setTimeout(() => {
		shouldShowPage = true;
	}, 2500);
</script>

{#if !shouldShowPage}
	<div
		class="absolute top-0 bottom-0 left-0 right-0 bg-black flex justify-center items-center"
		transition:fade
	>
		{#if shouldShowName}
			<div class="text-white">
				<span class="text-4xl font-semibold">Viktor Syrytsia </span>
				<span class="text-4xl"> ./ </span><span class="text-4xl font-thin">Web Developer</span>
			</div>
		{/if}
	</div>
{:else}
	<div transition:fade>
		<div class="page">
			<MainAnimation />
			<div class="menu">
				<div>
					<Menu />
				</div>
			</div>
			<div class="absolute top-0 left-0 right-0 bottom-0 z-20">
				<Transition url={$page.url}>
					<slot />
				</Transition>
			</div>
		</div>

		<div class="frame">
			<div class="hole" />
		</div>
	</div>
{/if}

<style>
	.page {
		@apply h-screen w-screen overflow-auto bg-white relative;
	}

	.frame {
		@apply z-30 fixed top-0 bottom-0 left-0 right-0 mix-blend-hard-light opacity-70 overflow-hidden pointer-events-none bg-white;
	}

	.hole {
		@apply z-40 absolute top-20 bottom-20 left-20 right-20 overflow-hidden pointer-events-none border border-gray-600 bg-gray-400;
	}
	.menu {
		width: 200px;
		height: 200px;
		top: calc(50% - 100px);
		left: calc(50% - 100px);
		@apply absolute z-50 flex justify-center items-center;
	}
</style>

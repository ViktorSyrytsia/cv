<script>
	import { animationColor } from './store/animation-color.store';
	function updateColor(colorSet) {
		console.log({ colorSet });
		animationColor.set(colorSet);
	}
</script>

<ul class="text-gray-900">
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#7f1d1d`, `#b91c1c`, `#ef4444`, `#fca5a5`, `#fee2e2`])}
			href="/">Home</a
		>
	</li>
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#064e3b`, `#047857`, `#10b981`, `#6ee7b7`, `#d1fae5`])}
			href="/expirience">Expirience</a
		>
	</li>
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#312e81`, `#4338ca`, `#6366f1`, `#a5b4fc`, `#e0e7ff`])}
			href="/skills">Skills</a
		>
	</li>
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#7c2d12`, `#c2410c`, `#f97316`, `#fdba74`, `#ffedd5`])}
			href="/contact">Contact</a
		>
	</li>
</ul>

<style lang="postcss">
	.menu-link {
		@apply text-lg p-2;
		transition: all 0.2s ease-in-out;
	}
	.menu-link:hover {
		transform: translateX(20px);
	}
</style>

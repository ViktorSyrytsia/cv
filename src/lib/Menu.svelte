<script>
	import { page } from '$app/stores';
	import { animationColor } from './store/animation-color.store';
	function updateColor(colorSet) {
		animationColor.set(colorSet);
	}
	const home = '/';
	const experience = '/experience';
	const skills = '/skills';
	const contact = '/contact';
</script>

<ul class="text-gray-900">
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#064e3b`, `#047857`, `#10b981`, `#6ee7b7`, `#d1fae5`])}
			href={home}
			class:active-home={$page.route.id === home}>Home</a
		>
	</li>
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#312e81`, `#4338ca`, `#6366f1`, `#a5b4fc`, `#e0e7ff`])}
			href={experience}
			class:active-experience={$page.route.id === experience}>Experience</a
		>
	</li>
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#7f1d1d`, `#b91c1c`, `#ef4444`, `#fca5a5`, `#fee2e2`])}
			href={skills}
			class:active-skills={$page.route.id === skills}>Skills</a
		>
	</li>
	<li class="menu-link">
		<a
			on:click={() => updateColor([`#7c2d12`, `#c2410c`, `#f97316`, `#fdba74`, `#ffedd5`])}
			href={contact}
			class:active-contact={$page.route.id === contact}>Contact</a
		>
	</li>
</ul>

<style lang="postcss">
	.menu-link {
		@apply text-lg p-2;
		transition: all 0.3s ease-in-out;
	}
	.menu-link:hover {
		transform: translateX(20px);
	}
	.active-home {
		color: #047857;
		@apply font-semibold;
	}
	.active-experience {
		color: #4338ca;
		@apply font-semibold;
	}
	.active-skills {
		color: #b91c1c;
		@apply font-semibold;
	}
	.active-contact {
		color: #c2410c;
		@apply font-semibold;
	}
	.menu-link a {
		transition: all 0.2s ease-in-out;
	}
</style>

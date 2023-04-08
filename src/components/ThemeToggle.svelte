<script lang="ts">
	import { IconMoonFilled, IconSunFilled } from "@tabler/icons-svelte";
	import { onMount } from "svelte";

	let theme: string = localStorage.getItem("theme") as string;
	if (!theme) theme = "dark";

	let size: number = 32;

	function changeTheme() {
		theme = theme !== "dark" ? "dark" : "light";
		localStorage.setItem("theme", theme);
		setTheme();
	}

	function setTheme() {
		document.documentElement.style.colorScheme = theme;
		document.body.className = theme;
	}

	onMount(() => {
		setTheme();
	});
</script>

<button class="theme-toggle flex-col" type="button" on:click={changeTheme}>
	{#if theme !== "dark"}
		<IconSunFilled {size} />
	{:else}
		<IconMoonFilled {size} />
	{/if}
</button>

<style>
	.theme-toggle {
		position: absolute;
		top: 0.5rem;
		right: 0.5rem;
	}

	.theme-toggle:hover {
		cursor: pointer;
	}
</style>

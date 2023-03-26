<script lang="ts">
	import { onMount } from "svelte";

	export let sender: string;
	export let message: string;

	const msgClass = `message ${sender} text-wrap`;
</script>

<article
	class={sender === "bot"
		? `${msgClass} theme-accent`
		: `${msgClass} theme-secondary`}
>
	{message}
</article>

<style>
	.message {
		padding: 1rem;
		max-width: 70%;
	}

	.message.bot {
		align-self: flex-start;
	}

	.message.user {
		align-self: flex-end;
	}
</style>

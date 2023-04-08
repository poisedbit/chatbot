<script lang="ts">
	export let sender: string;
	export let message: string;

	const msgClass = `message-log-entry ${sender} text-wrap`;
</script>

<article
	class={sender === "bot"
		? `${msgClass} theme-accent`
		: `${msgClass} theme-secondary`}
>
	{message}
</article>

<style>
	.message-log-entry {
		padding: 1rem;
		max-width: 70%;
	}

	.message-log-entry.bot {
		align-self: flex-start;
	}

	.message-log-entry.user {
		align-self: flex-end;
	}
</style>

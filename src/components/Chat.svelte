<script lang="ts">
	import eliza from "../chatbot";
	import MessageInputField from "./MessageInputField.svelte";
	import MessageLog from "./MessageLog.svelte";
	import MessageLogEntry from "./MessageLogEntry.svelte";

	let messages = [["bot", eliza.getInitial()]];

	function sendMessage(e: Event) {
		if (
			(e as KeyboardEvent).key === "Enter" &&
			!(e as KeyboardEvent).shiftKey
		) {
			e.preventDefault();

			const msg = (e.target as HTMLElement).innerText.trim();

			if (!msg || msg === "") return;

			const reply = eliza.transform(msg);
			messages = [...messages, ["user", msg]];

			(e.target as HTMLElement).innerText = "";

			messages = [...messages, ["bot", reply]];
		}
	}
</script>

<article class="chat flex-col theme-primary">
	<MessageLog>
		{#each messages as [sender, message]}
			<MessageLogEntry {sender} {message} />
		{/each}
	</MessageLog>
	<MessageInputField on:keydown={sendMessage} />
</article>

<style>
	.chat {
		width: 100%;
		height: 100%;
		padding: 1rem;
		align-items: center;
	}
</style>

<script>
	import MessageInputField from "./MessageInputField.svelte";
	import MessageLog from "./MessageLog.svelte";
</script>

<div class="chat-container flex-col dark-0">
	<MessageLog />
	<MessageInputField />
</div>

<style>
	.chat-container {
		width: 100%;
		height: 100%;
		padding: 1rem;
		align-items: center;
	}
</style>

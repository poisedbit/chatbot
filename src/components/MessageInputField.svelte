<script lang="ts">
	function autoResizeTextArea(e: Event) {
		const textarea = e.currentTarget as HTMLTextAreaElement;
		textarea.style.height = "auto";
		textarea.style.height = `${textarea.scrollHeight}px`;
	}
</script>

<div class="message-input-container flex-col">
	<textarea
		class="message-textarea dark-1"
		name="message-textarea"
		rows="1"
		on:input={autoResizeTextArea}
	/>
</div>

<style>
	.message-input-container {
		height: 10%;
		width: 100%;
		padding: 1rem 0;
	}

	.message-textarea {
		width: 100%;
		height: auto;
		padding: 1rem;
		border-radius: 0.25rem;
	}
</style>

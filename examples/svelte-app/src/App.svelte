<script lang="ts">
	import { metadata } from 'tauri-plugin-fs-extra-api'

	let path = '/'
	let response = ''

	function updateResponse(returnValue) {
		response += `[${new Date().toLocaleTimeString()}]` + (typeof returnValue === 'string' ? returnValue : JSON.stringify(returnValue)) + '<br>'
	}

	function _metadata() {
		metadata(path).then(updateResponse).catch(updateResponse)
	}
</script>

<div>
	<input bind:value={path} placeholder="Path to read metadata">
	<button on:click="{_metadata}">Get metadata</button>
	<div>{@html response}</div>
</div>
<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let text: string = '';
	export let id: number = 0;

	const dispatch = createEventDispatcher();

	const removeNote = (id: number) => {
		dispatch('remove-note', {
			id
		});
	};
</script>

<div class="card">
	<div class="card-body">
		<div class="d-flex justify-content-between align-items-center">
			<div>{text}</div>
			<button type="button" class="btn btn-danger" on:click={() => removeNote(id)}
				><svg
					xmlns="http://www.w3.org/2000/svg"
					width="16"
					height="16"
					fill="currentColor"
					class="bi bi-trash-fill"
					viewBox="0 0 16 16"
				>
					<path
						d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5M8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5m3 .5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 1 0"
					/>
				</svg></button
			>
		</div>
	</div>
</div>
<br />

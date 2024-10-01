<script lang="ts">
	export const ssr = false;
 
  import NewNote from "./components/new-note.svelte";
  import Note from "./components/note.svelte";

	let notes: string[] = JSON.parse(localStorage.getItem('notes') || '[]');

	const addNote = (text: string) => {
		notes = [...notes, text];
    localStorage.setItem('notes',JSON.stringify(notes))
	};

	const removeNote = (id: number) => {
		notes.splice(id, 1);
		notes = [...notes];
    localStorage.setItem('notes',JSON.stringify(notes))
	};
</script>

<div class="container">
	<br />
	<nav><h3>Svelte notekeeper</h3></nav>
	<hr />
</div>

<div class="container">
	<NewNote on:add-new-note={(event) => addNote(event.detail.text)} />
</div>

<br />

<div class="container">
	{#each notes as note, id}
		<Note text={note} {id} on:remove-note={(event) => removeNote(event.detail.id)} />
	{:else}
		<div class="alert alert-warning d-flex align-items-center" role="alert">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="16"
				height="16"
				fill="currentColor"
				class="bi bi-exclamation-circle-fill"
				viewBox="0 0 16 16"
			>
				<path
					d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0M8 4a.905.905 0 0 0-.9.995l.35 3.507a.552.552 0 0 0 1.1 0l.35-3.507A.905.905 0 0 0 8 4m.002 6a1 1 0 1 0 0 2 1 1 0 0 0 0-2"
				/>
			</svg> &nbsp; There are no notes!
		</div>
	{/each}
</div>

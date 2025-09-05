<script lang="ts">
	import { PaneGroup, Pane, PaneResizer } from 'paneforge';

	let test = $state(
		(
			await (await fetch('https://openlibrary.org/subjects/javascript.json?details=false')).json()
		).works.sort((a: { title: string }, b: { title: string }) => a.title.localeCompare(b.title)) ??
			[]
	);
</script>

<div class="h-full w-full p-8">
	<PaneGroup direction="horizontal" class="gap-4">
		<Pane defaultSize={50} class="border-border rounded-xl border p-2">
			{#each test as t}
				<p>{t.title}</p>
			{/each}
		</Pane>
		<PaneResizer class="my-8 w-2 rounded-xl border" />
		<Pane defaultSize={50} class="border-border rounded-xl border p-2">Pane</Pane>
	</PaneGroup>
</div>

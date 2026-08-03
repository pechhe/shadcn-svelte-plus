<script lang="ts">
	import AlertCircleIcon from "@lucide/svelte/icons/alert-circle";
	import CheckCircle2Icon from "@lucide/svelte/icons/check-circle-2";
	import FileCodeIcon from "@lucide/svelte/icons/file-code";
	import FileTextIcon from "@lucide/svelte/icons/file-text";
	import ImageIcon from "@lucide/svelte/icons/image";
	import LoaderIcon from "@lucide/svelte/icons/loader";
	import TableIcon from "@lucide/svelte/icons/table";
	import XIcon from "@lucide/svelte/icons/x";
	import * as Attachment from "$lib/registry/ui/attachment/index.js";
</script>

<div class="flex w-full max-w-xl flex-col gap-8">
	<div class="flex flex-col gap-3">
		<div class="px-1 text-xs font-medium text-muted-foreground">Files</div>
		<Attachment.Root class="w-full">
			<Attachment.Media><FileTextIcon /></Attachment.Media>
			<Attachment.Content>
				<Attachment.Title>sales-dashboard.pdf</Attachment.Title>
				<Attachment.Description>PDF · 2.4 MB</Attachment.Description>
			</Attachment.Content>
			<Attachment.Actions>
				<Attachment.Action aria-label="Remove sales-dashboard.pdf"><XIcon /></Attachment.Action>
			</Attachment.Actions>
		</Attachment.Root>
		<Attachment.Root class="w-full">
			<Attachment.Media><TableIcon /></Attachment.Media>
			<Attachment.Content>
				<Attachment.Title>customer-import.csv</Attachment.Title>
				<Attachment.Description>CSV · 18 KB</Attachment.Description>
			</Attachment.Content>
			<Attachment.Actions>
				<Attachment.Action aria-label="Remove customer-import.csv"><XIcon /></Attachment.Action>
			</Attachment.Actions>
		</Attachment.Root>
		<Attachment.Root class="w-full">
			<Attachment.Media><FileCodeIcon /></Attachment.Media>
			<Attachment.Content>
				<Attachment.Title>message-renderer.tsx</Attachment.Title>
				<Attachment.Description>TypeScript · 12 KB</Attachment.Description>
			</Attachment.Content>
			<Attachment.Actions>
				<Attachment.Action aria-label="Remove message-renderer.tsx"><XIcon /></Attachment.Action>
			</Attachment.Actions>
		</Attachment.Root>
	</div>

	<div class="flex flex-col gap-3">
		<div class="px-1 text-xs font-medium text-muted-foreground">Images and states</div>
		<div class="grid grid-cols-2 gap-3 sm:grid-cols-3">
			<Attachment.Root orientation="vertical">
				<Attachment.Media variant="image">
					<div
						class="size-full bg-gradient-to-br from-violet-400 via-fuchsia-500 to-orange-300"
					></div>
				</Attachment.Media>
				<Attachment.Content>
					<Attachment.Title>workspace.png</Attachment.Title>
					<Attachment.Description>PNG · 1.8 MB</Attachment.Description>
				</Attachment.Content>
			</Attachment.Root>
			<Attachment.Root size="sm" state="uploading">
				<Attachment.Media><LoaderIcon class="animate-spin" /></Attachment.Media>
				<Attachment.Content>
					<Attachment.Title>Uploading...</Attachment.Title>
					<Attachment.Description>42% complete</Attachment.Description>
				</Attachment.Content>
			</Attachment.Root>
			<Attachment.Root size="sm" state="error">
				<Attachment.Media><AlertCircleIcon /></Attachment.Media>
				<Attachment.Content>
					<Attachment.Title>Failed upload</Attachment.Title>
					<Attachment.Description>Try again</Attachment.Description>
				</Attachment.Content>
			</Attachment.Root>
			<Attachment.Root size="sm" state="done">
				<Attachment.Media><CheckCircle2Icon /></Attachment.Media>
				<Attachment.Content>
					<Attachment.Title>Completed</Attachment.Title>
					<Attachment.Description>Ready to send</Attachment.Description>
				</Attachment.Content>
			</Attachment.Root>
		</div>
	</div>

	<div class="flex flex-col gap-3">
		<div class="px-1 text-xs font-medium text-muted-foreground">Scrollable group</div>
		<Attachment.Group class="w-full">
			{#each ["design.fig", "brief.pdf", "assets.zip", "notes.txt"] as file (file)}
				<Attachment.Root orientation="vertical" size="sm">
					<Attachment.Media><ImageIcon /></Attachment.Media>
					<Attachment.Content>
						<Attachment.Title>{file}</Attachment.Title>
						<Attachment.Description>File · 2 MB</Attachment.Description>
					</Attachment.Content>
				</Attachment.Root>
			{/each}
		</Attachment.Group>
	</div>
</div>

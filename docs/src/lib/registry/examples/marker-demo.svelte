<script lang="ts">
	import CircleCheckIcon from "@lucide/svelte/icons/circle-check";
	import InfoIcon from "@lucide/svelte/icons/info";
	import SparklesIcon from "@lucide/svelte/icons/sparkles";
	import * as Marker from "$lib/registry/ui/marker/index.js";
</script>

<div class="flex w-full max-w-xl flex-col gap-6">
	<Marker.Root>
		<Marker.Icon><InfoIcon /></Marker.Icon>
		<Marker.Content>
			Your workspace is ready. <a href="/docs/components">Explore the components</a> to get started.
		</Marker.Content>
	</Marker.Root>
	<Marker.Root variant="border">
		<Marker.Icon><CircleCheckIcon /></Marker.Icon>
		<Marker.Content>All changes have been saved successfully.</Marker.Content>
	</Marker.Root>
	<Marker.Root variant="separator">
		<Marker.Icon><SparklesIcon /></Marker.Icon>
		<Marker.Content>New activity</Marker.Content>
	</Marker.Root>
</div>

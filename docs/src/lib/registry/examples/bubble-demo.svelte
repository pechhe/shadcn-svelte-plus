<script lang="ts">
	import HeartIcon from "@lucide/svelte/icons/heart";
	import ThumbsUpIcon from "@lucide/svelte/icons/thumbs-up";
	import * as Bubble from "$lib/registry/ui/bubble/index.js";
</script>

<div class="flex w-full max-w-xl flex-col gap-8">
	<div class="flex flex-col gap-3">
		<div class="px-1 text-xs font-medium text-muted-foreground">Conversation</div>
		<Bubble.Group class="w-full">
			<Bubble.Root variant="muted">
				<Bubble.Content>Hi! Can you review this layout for me?</Bubble.Content>
			</Bubble.Root>
			<Bubble.Root align="end" variant="default">
				<Bubble.Content>Absolutely. The spacing and hierarchy look good.</Bubble.Content>
				<Bubble.Reactions align="end">
					<button class="flex items-center gap-1 rounded-full px-2 py-1 text-xs" aria-label="Like">
						<ThumbsUpIcon class="size-3.5" /> 2
					</button>
				</Bubble.Reactions>
			</Bubble.Root>
			<Bubble.Root variant="tinted">
				<Bubble.Content>
					The tinted variant works well for assistant responses and supporting content.
				</Bubble.Content>
			</Bubble.Root>
		</Bubble.Group>
	</div>

	<div class="grid gap-3 sm:grid-cols-2">
		{#each [["secondary", "Secondary"], ["outline", "Outline"], ["ghost", "Ghost"], ["destructive", "Destructive"]] as [variant, label] (variant)}
			<Bubble.Root variant={variant as "secondary" | "outline" | "ghost" | "destructive"}>
				<Bubble.Content>{label} bubble with a short message.</Bubble.Content>
			</Bubble.Root>
		{/each}
	</div>

	<Bubble.Root align="end" variant="secondary">
		<Bubble.Content>
			<Bubble.Reactions side="top" align="end">
				<button class="flex items-center gap-1 rounded-full px-2 py-1 text-xs" aria-label="Love">
					<HeartIcon class="size-3.5 fill-current" /> 4
				</button>
			</Bubble.Reactions>
			A bubble can also contain a reaction row positioned above or below it.
		</Bubble.Content>
	</Bubble.Root>
</div>

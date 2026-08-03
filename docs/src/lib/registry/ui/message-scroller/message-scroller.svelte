<script lang="ts">
	import { cn, type WithElementRef } from "$lib/utils.js";
	import { useMessageScroller } from "./message-scroller.svelte.js";
	import type { HTMLAttributes } from "svelte/elements";

	const controller = useMessageScroller();
	let {
		ref = $bindable(null),
		class: className,
		children,
		...restProps
	}: WithElementRef<HTMLAttributes<HTMLDivElement>> = $props();

	$effect(() => {
		controller.setRoot(ref);
		return () => controller.setRoot(null);
	});
</script>

<div
	bind:this={ref}
	data-slot="message-scroller"
	class={cn(
		"group/message-scroller relative flex size-full min-h-0 flex-col overflow-hidden",
		className
	)}
	{...restProps}
>
	{@render children?.()}
</div>

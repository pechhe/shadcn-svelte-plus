<script lang="ts">
	import { cn, type WithElementRef } from "$lib/utils.js";
	import { useMessageScroller } from "./message-scroller.svelte.js";
	import type { HTMLAttributes } from "svelte/elements";

	const controller = useMessageScroller();
	let {
		ref = $bindable(null),
		class: className,
		messageId,
		scrollAnchor = false,
		children,
		...restProps
	}: WithElementRef<HTMLAttributes<HTMLDivElement>> & {
		messageId?: string;
		scrollAnchor?: boolean;
	} = $props();

	$effect(() => {
		const element = ref;
		const id = messageId;
		if (!element || !id) return;
		controller.registerItem(id, element);
		return () => controller.registerItem(id, null, element);
	});
</script>

<div
	bind:this={ref}
	data-slot="message-scroller-item"
	data-message-id={messageId}
	data-scroll-anchor={scrollAnchor ? "true" : "false"}
	class={cn(
		"min-w-0 shrink-0 [contain-intrinsic-size:auto_10rem] [content-visibility:auto]",
		className
	)}
	{...restProps}
>
	{@render children?.()}
</div>

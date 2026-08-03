<script lang="ts">
	import BotIcon from "@lucide/svelte/icons/bot";
	import UserIcon from "@lucide/svelte/icons/user";
	import * as Bubble from "$lib/registry/ui/bubble/index.js";
	import * as MessageScroller from "$lib/registry/ui/message-scroller/index.js";
	import * as Message from "$lib/registry/ui/message/index.js";

	type DemoMessage = { id: string; role: "user" | "assistant"; text: string };

	let messages = $state<DemoMessage[]>([
		{ id: "1", role: "user", text: "Can you summarize the new components?" },
		{
			id: "2",
			role: "assistant",
			text: "Attachment, Bubble, Marker, Message, Message Scroller, and Typeset are now available.",
		},
		{ id: "3", role: "user", text: "How should I validate the visual details?" },
		{
			id: "4",
			role: "assistant",
			text: "Scroll through this transcript, jump to the latest message, and try loading earlier history.",
		},
		{ id: "5", role: "user", text: "That makes sense. What about long responses?" },
		{
			id: "6",
			role: "assistant",
			text: "The viewport preserves your position when history is prepended and follows streamed output only while you remain at the live edge.",
		},
		{ id: "7", role: "user", text: "Great, I am ready to inspect the components." },
		{
			id: "8",
			role: "assistant",
			text: "Use the button in the lower corner to return to the latest message.",
		},
	]);

	let historyLoaded = $state(false);

	function loadHistory() {
		if (historyLoaded) return;
		historyLoaded = true;
		messages = [
			{
				id: "-2",
				role: "assistant",
				text: "Earlier context is preserved above the current transcript.",
			},
			{ id: "-1", role: "user", text: "I also wanted to ask about loading older messages." },
			...messages,
		];
	}
</script>

<div class="flex w-full max-w-xl flex-col gap-3">
	<div class="flex items-center justify-between gap-3 px-1 text-xs text-muted-foreground">
		<span>Scroll to test the live-edge button and anchoring.</span>
		<button
			type="button"
			class="shrink-0 font-medium text-foreground underline underline-offset-4 hover:text-primary"
			onclick={loadHistory}
		>
			{historyLoaded ? "History loaded" : "Load earlier"}
		</button>
	</div>

	<div class="h-[28rem] w-full overflow-hidden rounded-xl border bg-card">
		<MessageScroller.Provider
			autoScroll
			defaultScrollPosition="last-anchor"
			scrollPreviousItemPeek={32}
		>
			<MessageScroller.Root>
				<MessageScroller.Viewport aria-label="Demo conversation">
					<MessageScroller.Content class="gap-6 p-4">
						{#each messages as message (message.id)}
							<MessageScroller.Item messageId={message.id} scrollAnchor={message.role === "user"}>
								<Message.Root align={message.role === "user" ? "end" : "start"}>
									<Message.Avatar
										class={message.role === "user"
											? "size-8 bg-muted text-foreground"
											: "size-8 bg-primary text-primary-foreground"}
									>
										{#if message.role === "user"}
											<UserIcon class="size-4" />
										{:else}
											<BotIcon class="size-4" />
										{/if}
									</Message.Avatar>
									<Message.Content>
										<Bubble.Root
											align={message.role === "user" ? "end" : "start"}
											variant={message.role === "user" ? "default" : "muted"}
										>
											<Bubble.Content class="whitespace-pre-wrap">{message.text}</Bubble.Content>
										</Bubble.Root>
									</Message.Content>
								</Message.Root>
							</MessageScroller.Item>
						{/each}
					</MessageScroller.Content>
				</MessageScroller.Viewport>
				<MessageScroller.Button />
			</MessageScroller.Root>
		</MessageScroller.Provider>
	</div>
</div>

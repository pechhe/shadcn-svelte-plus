<script lang="ts">
	import BotIcon from "@lucide/svelte/icons/bot";
	import UserIcon from "@lucide/svelte/icons/user";
	import * as Bubble from "$lib/registry/ui/bubble/index.js";
	import * as Message from "$lib/registry/ui/message/index.js";
</script>

<div class="w-full max-w-xl">
	<Message.Group>
		<Message.Root>
			<Message.Avatar class="size-8 bg-primary text-primary-foreground">
				<BotIcon class="size-4" />
			</Message.Avatar>
			<Message.Content>
				<Message.Header>Assistant · just now</Message.Header>
				<Bubble.Root variant="muted">
					<Bubble.Content>
						I can help you compare the available components and choose the right composition.
					</Bubble.Content>
				</Bubble.Root>
				<Message.Footer>Helpful</Message.Footer>
			</Message.Content>
		</Message.Root>

		<Message.Root align="end">
			<Message.Avatar class="size-8 bg-muted text-foreground">
				<UserIcon class="size-4" />
			</Message.Avatar>
			<Message.Content>
				<Message.Header>You · just now</Message.Header>
				<Bubble.Root align="end" variant="default">
					<Bubble.Content>Show me a compact example with an avatar and metadata.</Bubble.Content>
				</Bubble.Root>
				<Message.Footer>Delivered</Message.Footer>
			</Message.Content>
		</Message.Root>

		<Message.Root>
			<Message.Avatar class="size-8 bg-muted text-muted-foreground">
				<BotIcon class="size-4" />
			</Message.Avatar>
			<Message.Content>
				<Bubble.Root variant="tinted">
					<Bubble.Content>
						Keep the message shell responsible for layout and let Bubble handle the visual
						treatment.
					</Bubble.Content>
				</Bubble.Root>
			</Message.Content>
		</Message.Root>
	</Message.Group>
</div>

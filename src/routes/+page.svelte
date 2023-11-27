<script>
	// @ts-nocheck

	import legend from '$lib/icons';
	import { slide } from 'svelte/transition';

	let message = '';
	$: words = message.split(' ');
</script>

<h1 class="text-2xl pt-2 print:pt-0 print:self-start print:text-black print:bg-white print:mt-0">
	CodeCrafter <span class="text-sm text-center hidden print:inline-block">by Arick Conley</span>
</h1>

<div class="flex-1 flex flex-col gap-8 w-full items-center print:top-10 print:absolute">
	<textarea
		rows="5"
		class="rounded-xl bg-white/10 py-2 px-3 resize-none w-3/4 text-xl font-bold
		tracking-wider print:hidden transition-all focus:scale-105 shadow-md focus:shadow-xl
		focus:ring-2 ring-offset-4"
		bind:value={message}
	></textarea>
	{#if !message}
		<div
			class="relative print:hidden text-2xl w-full px-4 text-white text-center font-sans h-full md:text-4xl md:py-12 grid
			justify-center items-center"
			transition:slide={{ start: 0.5, duration: 450 }}
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				xml:space="preserve"
				fill-rule="evenodd"
				stroke-linejoin="round"
				stroke-miterlimit="2"
				clip-rule="evenodd"
				viewBox="0 0 347 699"
				class="absolute w-48 md:w-96 top-0 left-[30%]"
				><path
					fill="#00b2ff"
					d="M165 685C117 640 2 488 0 398c-2-89 142-206 152-250 6-32-95-14-95-14L290 0l57 213s-78-46-106-23C204 220 82 317 81 
					397c0 85 153 158 187 204 15 20 38 58 21 72s-94 41-124 12Z"
				/></svg
			>
			<p class="z-10 drop-shadow-lg">
				Type a message into the box and create a fun cipher that your kids can decode.
			</p>
		</div>
	{/if}

	{#if message}
		<div class="flex justify-between flex-1 w-full">
			<div class="flex-1">
				<div class="flex flex-wrap gap-y-2 px-2 flex-1 overflow-x-scroll overflow-y-hidden">
					{#each words as word}
						<div class="flex gap-2 mr-8">
							{#each word as letter}
								<div class="flex flex-col text-4xl">
									{#if legend.find((value) => value.character == letter.toUpperCase())}
										<span
											class="border-b-2 h-12 border-blue-900 print:border-black text-white/30 print:text-transparent"
										>
											{letter}
										</span>
										<span class="material-symbols-outlined text-3xl md:text-5xl pt-1">
											{legend.find((value) => value.character == letter.toUpperCase())['icon']}
										</span>
									{:else}
										<span class="">{letter}</span>
									{/if}
								</div>
							{/each}
						</div>
					{/each}
				</div>
			</div>
			<div class="hidden md:grid grid-cols-2 gap-y-0.5 items-center font-normal print:grid">
				{#each legend as icon}
					<span class="px-2">{icon.character}</span>
					<span class="material-symbols-outlined text-3xl print:text-black print:text-2xl"
						>{icon.icon}
					</span>
				{/each}
			</div>
		</div>
	{:else}
		<p class="hidden print:block">You have to type your message before you print.</p>
	{/if}
</div>

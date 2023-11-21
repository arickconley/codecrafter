<script>
	const icons = [
		'settings',
		'grade',
		'key',
		'open_with',
		'assistant_navigation',
		'stat_0',
		'dialogs',
		'stat_3',
		'point_scan',
		'radio_button_partial',
		'person',
		'health_and_safety',
		'eco',
		'emoji_objects',
		'public',
		'rocket_launch',
		'cruelty_free',
		'thunderstorm',
		'solar_power',
		'bedtime',
		'sunny',
		'skull',
		'tornado',
		'volcano',
		'hand_bones',
		'tibia',
		'deceased',
		'playing_cards',
		'helicopter',
		'call',
		'photo_camera',
		'shopping_cart',
		'shopping_basket',
		'local_library',
		'cut',
		'mic',
		'music_note',
		'flight',
		'two_wheeler',
		'snowmobile',
		'directions_boat',
		'agriculture',
		'local_taxi',
		'sports_esports',
		'sports_gymnastics',
		'sports_basketball',
		'roller_skating',
		'sports_football',
		'sports_baseball',
		'sports_soccer',
		'paragliding',
		'toys_fan',
		'fertile',
		'smart_toy',
		'headphones',
		'phone_iphone',
		'memory',
		'videogame_asset',
		'shield',
		'icecream',
		'luggage',
		'lunch_dining',
		'trip',
		'your_trips',
		'mop',
		'chair',
		'ac_unit',
		'yard',
		'sprinkler',
		'crib',
		'mode_heat',
		'child_care',
		'skillet',
		'tools_power_drill'
	];

	const legend = icons
		.map((value) => ({ value, sort: Math.random() }))
		.sort((a, b) => a.sort - b.sort)
		.map(({ value }) => value)
		.slice(0, 26)
		.map((value, i) => ({ character: String.fromCharCode(i + 65), icon: value }));

	let message = '';
	$: words = message.split(' ');
</script>

<h1 class="text-2xl pt-2 print:pt-0 print:self-start">
	CodeCrafter <span class="text-sm hidden print:inline-block">by Arick Conley</span>
</h1>

<div class="flex-1 flex flex-col gap-8 w-full items-center print:top-10 print:absolute">
	<textarea
		rows="5"
		class="rounded-xl bg-white/10 py-2 px-3 resize-none w-3/4 text-xl font-bold tracking-wider print:hidden"
		bind:value={message}
	></textarea>

	<div class="flex justify-between flex-1 w-full">
		<div class="flex-1">
			<div class="flex flex-wrap flex-1 overflow-x-scroll overflow-y-hidden">
				{#each words as word}
					<div class="flex gap-2 mr-6">
						{#each word as letter}
							<div class="flex flex-col text-4xl">
								{#if legend.find((value) => value.character == letter.toUpperCase())}
									<span class="h-16 w-12 border-b-2 border-blue-900"></span>
									<span class="material-symbols-outlined text-5xl pt-1">
										{legend.find((value) => value.character == letter.toUpperCase())['icon']}
									</span>
								{:else}
									<span class="h-4 w-12">{letter}</span>
								{/if}
							</div>
						{/each}
					</div>
				{/each}
			</div>
		</div>
		<div class="flex flex-col justify-between font-normal max-h-screen">
			{#each legend as icon}
				<div class="flex justify-center items-center">
					<span class="px-2">{icon.character}</span>
					<span class="material-symbols-outlined text-3xl">{icon.icon}</span>
				</div>
			{/each}
		</div>
	</div>
</div>

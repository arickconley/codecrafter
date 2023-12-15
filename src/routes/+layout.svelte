<script>
	import '../app.css';
	import { onMount } from 'svelte';

	onMount(() => {
		if (
			localStorage.theme === 'dark' ||
			(!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)
		) {
			document.documentElement.classList.add('dark');
		} else {
			document.documentElement.classList.remove('dark');
		}
	});
</script>

<svelte:head>
	<title>CodeCrafter</title>
</svelte:head>

<button
	on:click={() => window.print()}
	class="fixed left-4 top-4 p-2 bg-blue-600 rounded-full flex justify-center items-center print:hidden"
>
	<span class="material-symbols-outlined text-blue-100">print</span>
	<span class="absolute material-symbols-outlined animate-ping text-blue-200">print</span>
</button>

<div class="flex flex-col w-full justify-between items-center container gap-8 font-fun font-bold">
	<slot />
</div>

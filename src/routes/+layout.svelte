<script>
	/** @type {import('./$types').LayoutData} */
	export let data;

	import '../app.css';
</script>

<div
	class="flex flex-col w-full text-white justify-between items-center container gap-8 font-fun font-bold"
>
	<slot />
</div>

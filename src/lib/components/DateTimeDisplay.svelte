<script lang="ts">
	import { P } from 'flowbite-svelte';

	export let date: string;
	let { class: className = '' } = $$props;
</script>

<div>
	<P weight="bold" color="text-white" align="right" size="2xl" class={className}>{date}</P>
</div>

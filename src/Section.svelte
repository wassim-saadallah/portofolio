<script lang="ts">
	import { slide } from 'svelte/transition';

	export let sectionName: string;
</script>

<style scoped>
	.section {
		height: 200vh;
		background-color: sandybrown;
		overflow: auto; /* h1 padding hack */
	}
</style>

<div transition:slide={{ duration: 1000 }} class="section">
	<h1>This is a section named {sectionName}</h1>
</div>

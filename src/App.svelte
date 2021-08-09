<script lang="ts">
	import Section from './Section.svelte';
	let openSections: string[] = [];
	// TODO: change scroll behavior to make it 
	// scroll by the height of the section if it's less
	// than the viewport length else we scroll to the top
	// (we need to know the height of sections beforehand)
	function toggleSection(
		name: string,
		ev: MouseEvent & { currentTarget: EventTarget & HTMLSpanElement }
	): void {
		openSections.push(name);
		openSections = openSections;
		ev.currentTarget.scrollIntoView({
			// top: ev.currentTarget.offsetTop,
			behavior: 'smooth',
		});
		console.log({ name, openSections });
	}
</script>

<style scoped>
	main {
		font-weight: 900;
		font-style: normal;
		line-height: 1.2;
		font-size: 4rem;

		text-align: start;
		padding: 20px;
	}

	.keyword {
		color: red;
		cursor: pointer;
		display: inline-block;
		position: relative;
	}

	.keyword:after {
		content: '';
		position: absolute;
		width: 100%;
		transform: scaleX(0);
		height: 0.1em;
		bottom: 0;
		left: 0;
		background-color: red;
		transform-origin: bottom right;
		transition: transform 0.25s ease-out;
	}

	.keyword:hover:after {
		transform: scaleX(1);
		transform-origin: bottom left;
	}

	@media screen and (max-width: 480px) {
		main {
			font-size: 2rem;
		}
	}
</style>

<main>
	have been working with web development since 2010, the period during which I
	have worked in different environments, from big consultancy companies to
	start-ups. I am a self-motivated and self-taught professional who likes to
	solve problems. I merge a passion for usability and user experience with
	technical knowledge to create cool digital
	<span on:click={(ev) => toggleSection('section 1', ev)} class="keyword">
		experiences
	</span>
	.
	{#if openSections.includes('section 1')}
		<Section sectionName="section 1" />
	{/if}
	My repertoire includes programming languages and tools such as ReactJS,
	EmberJS, Mobx, Wordpress, SailsJS, MySQL, PostgreSQL, Nginx and Apache server
	configuration, Gulp, SASS, LESS, Twitter Bootstrap, Susy, jQuery, and more.
	Almost before we knew it, we had left the ground. If you are intrigued, we can
	<span on:click={(ev) => toggleSection('section 2', ev)} class="keyword">
		catch up
	</span>
	{#if openSections.includes('section 2')}
		<Section sectionName="section 2" />
	{/if}
	and work together :D.
</main>

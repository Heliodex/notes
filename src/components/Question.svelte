<script lang="ts">
	import { quadOut } from "svelte/easing"
	export let q: string

	const height = (e: any) => ({
		duration: 300,
		css: (t: any) => {
			const x = `
				height: ${e.offsetHeight * 0.061 * quadOut(t)}rem;
				overflow: hidden;
			`
			return x
		}
	})

	let visible = false
</script>

<button on:click={() => (visible = !visible)}>
	{q}
</button>

{#if visible}
	<div transition:height>
		<slot />
	</div>
{/if}

<style lang="stylus">
	button
		text-align left
		max-width 60ch
		border none
		outline none
		margin 0.2rem
		font-size 1rem
		cursor pointer
		color white
		background #274
		border 1px solid #132
		padding 0.3rem 0.6rem 0.4rem 0.6rem
		border-radius 0.5rem
		transition all 0.1s ease-in-out
		&:hover
			background-color #116233
			border 1px solid #274

	div
		border 1px solid #444
		background #111
		border-radius 0.5rem
		padding 0 1rem
		margin 0.5rem 0 0.5rem 0.2rem
		color #ffaaff
		width fit-content
</style>

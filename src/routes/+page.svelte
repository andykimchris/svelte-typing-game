<script lang="ts">
type Game = 'waiting for input' | 'in progress' | 'game over'
type Word = 'string'

let game: Game = "waiting for input"
let typedLetter = ''

let words: Word[] = "The quick brown fox jumps over the lazy dog".split(' ')

  let wordIndex = 0
  let letterIndex = 0
  let correctLetters = 0

  let wordsEl: HTMLDivElement
  let letterEl: HTMLSpanElement
  let inputEl: HTMLInputElement

	function handleKeyDown(e: KeyboardEvent) {
		if (e.keyCode === 'Space') e.preventDefault();

		if (game === "waiting for input") startGame();
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<div class="game" data-game={game}>
		<input bind:this={inputEl} bind:value={typedLetter} on:input={updateGameState} on:keydown={handleKeyDown} class="input" type="text" />

		<div class="words" bind:this={wordsEl}>
			{#each words as word}
				<span class="word">
					{#each word as letter}
						<span class="letter">{letter}</span>
					{/each}
				</span>
			{/each}
		</div>
	</div>
</section>

<style lang="scss">
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
		color: pink;
		span {
			color: purple;
		}
	}


</style>

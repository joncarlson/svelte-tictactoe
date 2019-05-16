<script>
	import Board from './Board.svelte'
	import { gameState, DRAW } from './store.js'

	function onSquareClick(e) {
		let index = e.target.dataset.index
		gameState.giveSquareToCurrentPlayer(index)
	}
</script>

<style>
	.game {
		display: flex;
		flex-direction: row;
	}

	.game-info {
		margin-left: 20px;
	}
</style>

<div class="game">
	<div class="game-board">
		<Board squares={$gameState.squares} on:click={onSquareClick} />
	</div>

	<div class="game-info">
		{#if $gameState.winningPlayer === DRAW}
			<p>GAME OVER: it's a draw!</p>
		{:else if $gameState.winningPlayer}
			<p>GAME OVER: Player <strong>{$gameState.winningPlayer}</strong> won!</p>
		{:else}
			<p>Current player is: {$gameState.currentPlayer}</p>
		{/if}
		
		<p><button on:click={gameState.reset}>Start a new game</button></p>
	</div>
</div>

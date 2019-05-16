<script>
	import Board from './Board.svelte'
	import { gameState } from './store.js'

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
		<p>Current player is: {$gameState.currentPlayer}</p>
		<p>Winning player is: {$gameState.winningPlayer}</p>
		<p><button on:click={gameState.reset}>Start a new game</button></p>
	</div>
</div>

<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-lg-12">
          <div class="row">
            <div class="col-lg-4">
              <GameBoard @getPositions="getPositions"/>
            </div>
            <div class="col-lg-8">
              <GameActions :moves="moves" @addMove="setMove"/>
            </div>
          </div>
          <div class="col-lg-3">
            <div class="row mt-2">
              <button @click="move" class="btn btn-sm btn-primary btn-block">Execute</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GameBoard from "./components/GameBoard.vue";
import GameActions from "./components/GameActions.vue";

export default {
  name: "app",
  data() {
    return {
      rowsAmount: 6,
      columnsAmount: 6,
      moves: [],
      positions: []
    };
  },
  components: {
    GameBoard,
    GameActions
  },
  methods: {
    setMove(move) {
      this.moves.push(move);
    },
    getPositions(positions) {
      this.positions = positions;
    },
    $_invalidMove(index) {
      this.moves.splice(index, 1);
      alert("Invalid move");
    },
    move() {
      const moves = this.moves;
      const positions = this.positions;

      // initial position
      let x = 1;
      let y = 1;

      for (const moveIndex in moves) {
        let move = moves[moveIndex];
        // update old position
        this.positions[x][y].hasCharacter = false;

        x = x + move.x;
        y = y + move.y;

        if (x < 1) {
          x = 1;
          this.$_invalidMove(moveIndex);
        } else if (x > this.rowsAmount) {
          x = this.rowsAmount;
          this.$_invalidMove(moveIndex);
        } else if (y < 1) {
          y = 1;
          this.$_invalidMove(moveIndex);
        } else if (y > this.columnsAmount) {
          y = this.columnsAmount;
          this.$_invalidMove(moveIndex);
        } else {
          this.positions[x][y].hasCharacter = true;
        }
      }
    }
  }
};
</script>
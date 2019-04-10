<template>
  <div>
    <div v-for="row in rowsAmount" :key="row" class="row">
      <div v-for="column in columnsAmount" :key="column">
        <SquareBoard :position="positions[row][column]"/>
      </div>
    </div>
  </div>
</template>

<script>
import SquareBoard from "./SquareBoard.vue";

export default {
  name: "GameBoard",
  props: {
    rowsAmount: {
      type: Number,
      default: 6
    },
    columnsAmount: {
      type: Number,
      default: 6
    }
  },
  data() {
    return {
      positions: []
    };
  },
  components: {
    SquareBoard
  },
  created() {
    const rows = this.rowsAmount;
    const columns = this.columnsAmount;
    const positions = [];

    for (let row = 1; row < rows + 1; row++) {
      positions[row] = [];

      for (let column = 1; column < columns + 1; column++) {
        positions[row][column] = {
          row: row,
          column: column,
          hasCharacter: false
        };
      }
    }

    this.positions = positions;
    this.$emit("getPositions", positions);
  }
};
</script>

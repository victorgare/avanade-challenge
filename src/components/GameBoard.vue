<template>
  <div>
    <div v-for="row in rowsAmount" :key="row" class="row">
      <SquareBoard v-for="column in columnsAmount" :key="column" :x="row" :y="column"/>
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
    return {};
  },
  components: {
    SquareBoard
  }
};
</script>

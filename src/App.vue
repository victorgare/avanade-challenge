<template>
  <div id="app">
    <div class="container">
      <div class="col-lg-12">
        <div class="col-lg-6">
          <GameBoard />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GameBoard from "./components/GameBoard.vue";
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  components: {
    GameBoard
  }
};
</script>
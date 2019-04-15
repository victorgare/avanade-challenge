<template>
  <div class="square">
    <span v-html="showFinishLine"></span>

    <span class="list-item" v-html="showCharacter"></span>
  </div>
</template>

<script>
export default {
  name: "SquareBoard",
  props: {
    position: {
      row: 0,
      column: 0,
      hasCharacter: false,
      isFinishLine: false
    }
  },
  computed: {
    showCharacter() {
      const hasCharacter = this.position.hasCharacter;

      if (hasCharacter) {
        return "<img class='img-fluid img-100 img-character' src='./src/assets/spaceship.png' />";
      }
    },
    showFinishLine() {
      const isFinishLine = this.position.isFinishLine;
      const hasCharacter = this.position.hasCharacter;
      let cssClass = "";

      if (hasCharacter) {
        cssClass = "img-finishline";
      }
      if (isFinishLine) {
        return `<img class='img-fluid img-100 ${cssClass}' src='./src/assets/blackhole.png' />`;
      }
    }
  }
};
</script>

<style scoped>
.square {
  background: gray;
  border: 1px solid #999;
  float: left;
  font-size: 24px;
  font-weight: bold;
  line-height: 34px;
  height: 50px;
  margin-right: -1px;
  margin-top: -1px;
  padding: 0;
  text-align: center;
  width: 50px;
  position: relative;
}
</style>

<style>
.img-100 {
  height: 100%;
  width: 100%;
}

.img-finishline {
  position: absolute;
  z-index: 2;
}

.img-character {
  position: relative;
  z-index: 2;
}
</style>


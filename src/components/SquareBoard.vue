<template>
  <div class="square">{{showCharacter}}</div>
</template>

<script>
export default {
  name: "SquareBoard",
  props: {
    position: {
      row: 0,
      column: 0,
      hasCharacter: false
    }
  },
  computed: {
    showCharacter() {
      const hasCharacter = this.position.hasCharacter;
      if (hasCharacter) {
        return hasCharacter;
      }
    }
  }
};
</script>

<style scoped>
.square {
  background: #fff;
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
}
</style>

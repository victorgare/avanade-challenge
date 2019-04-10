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


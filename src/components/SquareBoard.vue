<template>
  <div @click="onClick" class="square col-md-1"></div>
</template>

<script>
export default {
  name: "SquareBoard",
  props: {
    x: Number,
    y: Number
  },
  methods: {
    onClick() {
      const x = this.x;
      const y = this.y;
      console.log(`X: ${x} | Y: ${y}`);
    }
  }
};
</script>


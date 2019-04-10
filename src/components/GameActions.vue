<template>
  <div>
    <div class="row">
      <div class="col-lg-4">
        <hr class="invisible">
        <div class="form-horizontal">
          <GameAction @dragged="handleEmit" :x="0" :y="-1" v-bind:tipo="'left'"/>
          <GameAction @dragged="handleEmit" :x="0" :y="1" v-bind:tipo="'right'"/>
          <GameAction @dragged="handleEmit" :x="-1" :y="0" v-bind:tipo="'up'"/>
          <GameAction @dragged="handleEmit" :x="1" :y="0" v-bind:tipo="'down'"/>
        </div>
      </div>

      <div class="col-lg-8">
        <div class="col-lg-6">
          <div class="row">
            <h3>Hints!</h3>
          </div>
        </div>
        <div class="dropzone" v-on:drop="onDrop($event)" v-on:dragover="allowDrop($event)">
          <div v-for="(element, index) in htmlElementsList" :key="index" :class="element"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GameAction from "./GameAction.vue";
import { log } from "util";

export default {
  name: "GameActions",
  props: {
    moves: Array
  },
  data() {
    return {
      draggingItem: undefined,
      elementHtml: "",
      htmlElementsList: []
    };
  },
  methods: {
    $_addMove(move) {
      // const move = { x, y };
      this.$emit("addMove", move);
    },
    handleEmit(obj) {
      this.draggingItem = obj.item;
      this.elementHtml = obj.html;
    },
    allowDrop(event) {
      event.preventDefault();
    },
    onDrop(event) {
      event.preventDefault();

      this.$_addMove(this.draggingItem);
      this.htmlElementsList.push(this.elementHtml);
      console.log(this.htmlElementsList);
    }
  },
  components: {
    GameAction
  }
};
</script>

<style scoped>
.dropzone {
  border: 2px solid black;
  min-height: 300px;
  padding: 5px;
}
</style>

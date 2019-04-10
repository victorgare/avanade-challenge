<template>
  <div>
    <div class="pt-1">
      <div
        v-on:dragstart="dragstart({x: x, y: y}, $event)"
        v-on:dragend="dragend($event)"
        draggable="true"
        :class="arrowClass"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GameAction",
  props: {
    x: {
      type: Number,
      required: true
    },
    y: {
      type: Number,
      required: true
    },
    tipo: {
      type: String,
      required: true,
      validator: function(value) {
        return ["up", "down", "left", "right"].indexOf(value) !== -1;
      }
    }
  },
  methods: {
    dragstart: function(item, e) {
      e.target.style.opacity = 0.5;

      this.$emit("dragged", {
        item: item,
        html: e.srcElement.className
      });
    },
    dragend: function(e) {
      e.target.style.opacity = 1;
    }
  },
  computed: {
    arrowClass() {
      let baseClass = "btn btn-sm btn-primary btn-block";

      switch (this.tipo) {
        case "up":
          baseClass += " seta-cima";
          break;

        case "left":
          baseClass += " seta-esquerda";
          break;

        case "right":
          baseClass += " seta-direita";
          break;

        case "down":
          baseClass += " seta-baixo";
          break;
      }

      return baseClass;
    }
  }
};
</script>

<style scoped>
.seta-esquerda:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0;
  height: 0;
  border-top: 5px solid transparent;
  border-bottom: 5px solid transparent;
  border-right: 5px solid white;
}

.seta-direita:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0;
  height: 0;
  border-top: 5px solid transparent;
  border-bottom: 5px solid transparent;
  border-left: 5px solid white;
}

.seta-cima:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-bottom: 5px solid white;
}

.seta-baixo:before {
  content: "";
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid white;
}
</style>


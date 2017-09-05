<template>

  <div class="game-board">

    <div v-for="row in height" class="row">

      <div
        v-for="col in width"
        :x="col"
        :y="row"
        class="cell"
        :index="getIndex(col, row)"
        :style="{ 'background-color': colors[(getIndex(col, row) - row) % colors.length] }"
        >



      </div>

    </div>

  </div>

</template>

<script>

export default {
  props: {
    colors: {
      default: ['#fff', '#000'],
      type: Array
    },
    width: {
      default: 8,
      type: Number
    },
    height: {
      default: 8,
      type: Number
    }
  },
  methods: {
    getIndex (col, row) {
      return (row - 1) * this.height + col
    }
  }
}

</script>

<style>

.cell {
  display: inline-block;
  width: 100px;
  height: 100px;
  border: 2px solid #000;
}

</style>

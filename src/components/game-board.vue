<template>

  <div class="game-board" :cellClicked="cellClicked(args)">

    <div v-for="row in height" class="row" :cellClicked="cellClicked(args)">

      <div
        v-for="col in width"
        :x="col"
        :y="row"
        class="cell"
        :index="getIndex(col, row)"
        :style="{ 'background-color': colors[(getIndex(col, row) - row) % colors.length] }"
        @click="cellClicked({ x: col, y: row, index: getIndex(col, row) })"
        >



      </div>

    </div>

  </div>

</template>

<script>

export default {
  props: {
    colors: {
      default: () => { return ['#fff', '#000'] },
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
    },
    cellClicked (args) {
      this.$emit('cellClicked', args)
    },
    passToParent (args) {
      this.$emit('cell-clicked', args)
    }
  }
}

</script>

<style scoped>

.game-board {
  font-size: 0;
  border: 1px solid #000;
  display: inline-block;
}
.cell {
  display: inline-block;
  width: 100px;
  height: 100px;
  line-height: 0;
}

</style>

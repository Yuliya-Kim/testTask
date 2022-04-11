<template>
  <div class="control-group">
    <div
      v-bind:class="setControlBtnClasses(control.name)"
      v-for="control in Controls.controls" :key="control.id"
      v-on:click="getDirection(control), doMove(direction)"
    >
      <button v-if="control.type === '__button'">{{control.name}}</button>
    </div>
  </div>
  <br>
  <h2>Действия</h2>
  <div class="actions-list">
    <ol type="1">
      <li class="actions-list__item" v-for="(movement, i) in movementsArr" :key="i">
        <span v-if="movement == 'u'">"So, and we go <b>up</b>!"</span>
        <span v-if="movement == 'r'">"So, and we go <b>right</b>!"</span>
        <span v-if="movement == 'd'">"So, and we go <b>down</b>!"</span>
        <span v-if="movement == 'l'">"So, and we go <b>left</b>!"</span>
      </li>
    </ol>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ContentControls',
  data() {
    return {
      Controls: Object,
      direction: null,
      movementResponse: null,
      checkReq: false,
      movementsArr: [],
    }
  },
  methods: {
    getDirection(control) {
      this.direction = control.request.direction
    },
    doMove(direction) {
      axios
        .post('/', {requestedFuncIndex: 6, direction: direction})
        .then(response => {
          this.movementsArr.push(response.data.direction)
        })
    },
    setControlBtnClasses: function (name) {
      if (name === "Move left") {
        return "btn left";
      } else if (name === "Move right") {
        return "btn right";
      } else if (name === "Move up") {
        return "btn up";
      } else if (name === "Move down") {
        return "btn down";
      }
    }
  },
  mounted() {
    axios
      .post('/', {requestedFuncIndex: 3})
      .then(response => {
        this.Controls = response.data
      })  
  }
}
</script>

<style scoped>

.control-group {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-column-gap: 10px;
  grid-row-gap: 10px;
}   

.left { grid-area: 2 / 1 / 3 / 2; }
.right { grid-area: 2 / 3 / 3 / 4; }
.up { grid-area: 1 / 2 / 2 / 3; }
.down { grid-area: 3 / 2 / 4 / 3; }

.btn > button {
  color: rgb(59, 59, 59);
  font-weight: 600;
}

.actions-list {
  height: 150px;
  padding: 10px;
  background: white;
  border: 1px solid lightgrey;
  border-radius: 10px;
  overflow-y: scroll;
}
</style>

<template>
  <div id="app">
    <button class="btn btn--minus" @click="minus">-</button>
    <span id="number" :class="{ disabled: reachesLimit }">{{ number }}</span>
    <button class="btn btn--plus" @click="add">+</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      number: 0
    }
  },
  computed: {
    reachesMinimal () {
      return this.number <= 0
    },
    reachesMaximum () {
      return this.number >= 10
    },
    reachesLimit () {
      return this.reachesMinimal || this.reachesMaximum
    }
  },
  methods: {
    add () {
      if (this.reachesMaximum) {
        return false
      }
      this.number++
    },
    minus () {
      if (this.reachesMinimal) {
        return false
      }
      this.number--
    }
  }
}
</script>

<style>
#app {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 32px;
}

#app > * + * {
  margin-left: 8px;
}

.btn {
  background: transparent;
  border: 2px solid gray;
  padding: 6px 8px;
  line-height: 16px;
  font-size: 20px;
  border-radius: 6px;
  cursor: pointer;
}

#number {
  width: 100px;
  border: 2px solid gray;
  padding: 6px 8px;
  line-height: 16px;
  text-align: center;
  border-radius: 6px;
}

.disabled {
  background-color: #faa;
}
</style>

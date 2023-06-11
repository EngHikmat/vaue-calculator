<template>
  <div class="container">
    <div>
      <div class="cal-header"><input type="text" v-model="result" @change="calculate" /></div>
      <div class="cal-content">
        <div class="percent">%</div>

        <div @click="clear">C</div>
        <div @click="backwords">&#8656;</div>
        <div class="one-divide">1/x</div>
        <div class="root">X</div>
        <div class="square-root">&#8730;</div>
        <div @click="set('/')">&#247;</div>
        <div @click="set(7)">7</div>
        <div @click="set(8)">8</div>
        <div @click="set(9)">9</div>
        <div @click="set('*')">&times;</div>
        <div @click="set(4)">4</div>
        <div @click="set(5)">5</div>
        <div @click="set(6)">6</div>
        <div @click="set('-')">-</div>
        <div @click="set(1)">1</div>
        <div @click="set(2)">2</div>
        <div @click="set(3)">3</div>
        <div @click="set('+')">+</div>
        <div>+/-</div>
        <div @click="set(0)">0</div>
        <div>.</div>
        <div class="mark" @click="calculate()">=</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: 0
    }
  },
  methods: {
    set(val) {
      if (typeof val != 'string') {
        if (this.result == 0) {
          this.result = val
        } else {
          this.result = this.result + val.toString()
        }
      } else {
        this.result = this.result + val.toString()
      }
    },
    calculate(e) {
      if (e === undefined) {
        this.result = eval(this.result)
      } else {
        this.result = eval(e.target.value)
      }

      // console.log(eval(e.target.value))
    },
    clear() {
      this.result = 0
    },
    backwords() {
      if (this.result.length === 1 || this.result == 0) {
        this.result = 0
      } else {
        this.result = this.result.slice(0, -1)
      }
    }
  }
}
</script>

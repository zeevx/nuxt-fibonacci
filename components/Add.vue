<template>
  <div>
    <form @submit="makeSequence" id="add-form">
        <div class="col-md-12">
          <div class="input-group">
            <input type="number" class="form-control" v-model="next" name="next" placeholder="Add First/Next Number" >
              <div class="input-group-append">
                <input type="submit" class="btn btn-success" value="Add">
              </div>
          </div>
            <small id="next" class="form-text text-muted">Input the first/next number you want in the sequence.</small>
        </div>
      </form>
      <div v-for="seqx in seq" v-bind:key="seqx.id">
        {{ seqx.value }},
      </div>
  </div>
</template>
<script>
import { v4 as uuidv4 } from 'uuid'
export default {
  name: 'Add',
  props: {
    sequence: Array,
    max: Number
  },
  data () {
    return {
      next: '',
      seq: [
        {
          id: 1,
          value: 7
        }
      ]
    }
  },
  /* eslint-disable no-unused-vars */

  methods: {
    makeSequence (e) {
      const gmax = window.max
      e.preventDefault()
      const newSequence = {
        id: uuidv4(),
        value: this.next
      }
      const num = this.next
      const a = Math.sqrt(5 * (num * num) - 4)
      const b = Math.sqrt(5 * (num * num) + 4)
      if (!gmax || gmax === '' || gmax === 0) {
        alert('Max Number cannot be empty or zero(0)!')
      } else if ((a - Math.floor(a)) === 0 || (b - Math.floor(b)) === 0 || num < this.max) {
        alert('Correct!! Add another fibonacci number!')
        this.$emit('add-seq', newSequence)
        const af = document.getElementById('add-form')
        af.reset()
      } else {
        alert('This is not a Fibonacci Number!')
      }
    }
  }
  /* eslint-disable no-unused-vars */
}
</script>
<style scoped>

</style>

<template>
  <div class="container">
    <div>
      <br>
      <Logo />
      <h1 class="title">
        Nuxt Fibonacci
      </h1>
    </div>
    <br>
    <div>
    <div class="form-group row">
      <Add v-on:add-seq="addNewSeq" :seq="sequences" :max="newmax"/>
      <Max v-on:add-max="addNewMax" :max="newmax"/>
      <div class="col-md-4">
          <button type="submit" v-on="view_seq" class="btn btn-success">View Sequence?</button>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import Add from '../components/Max.vue'
import Max from '../components/Add.vue'

export default {
  data () {
    return {
      newmax: '',
      sequences: []
    }
  },
  components: {
    Add,
    Max
  },
  methods: {
    addNewMax (newMax) {
      this.newmax = newMax
    },
    addNewSeq (newSequence) {
      this.sequences = [...this.sequences, newSequence]
    },
    view_seq () {
      return true
    }
  }
}
/* eslint-disable */
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

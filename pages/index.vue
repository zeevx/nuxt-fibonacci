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
      <form @submit="add">
        <div class="col-md-12">
            <div class="input-group">
              <input
              type="number"
              class="form-control"
              style=""
              v-model="max"
               name="max"
              placeholder="Max Number">
              <div class="input-group-append">
                    <input type="submit" class="btn btn-success" value="Max">
              </div>
            </div>
        <small id="max" class="form-text text-muted">Input the maximum number you want in the sequence.</small>
        </div>
      </form>
      <form @submit="add">
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
      <div class="col-md-4">
          <button type="submit" class="btn btn-success">Submit</button>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import uuid from 'uuid'
export default {
  data () {
    return {
      max: '',
      next: '',
      sequence: []
    }
  },
  components: {
  },
  /* eslint-disable no-unused-vars */

  methods: {
    makeSequence (e) {
      e.preventDefault()
      const newSequence = {
        id: uuid.v4(),
        max: this.max,
        next: this.next
      }
      this.$emit(newSequence)
      this.max = ''
    },
    addNew (makeSequnce) {
      this.sequence = [...this.sequence, makeSequnce]
    }
  }
  /* eslint-disable no-unused-vars */

}
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

<template>
  <div>
    <form @submit="makeMax" id="max-form">
          <div class="col-md-12">
              <div class="input-group">
                <input
                type="number"
                class="form-control"
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
    <div>
       Max Inputed: {{ max }}
    </div>

  </div>
</template>
<script>
export default {
  name: 'Max',
  props: {
    max: Number
  },
  /* eslint-disable no-unused-vars */

  methods: {
    makeMax (e) {
      e.preventDefault()
      const newMax = this.max
      window.max = newMax
      this.$emit('add-max', newMax)
      const mf = document.getElementById('max-form')
      mf.reset()
      // this.max = ''
    }
  }
  /* eslint-disable no-unused-vars */
}
</script>
<style scoped>

</style>

<template>
  <div>
    <h1>My todo list</h1>
	<input
    type="text"
    class="input"
	:value="value"
    v-on="listeners"
  >
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
	value: {
	type: String,
	default: '',
	}
  },
  computed: {
    listeners () {
      return {
        // Pass all component listeners directly to input
        ...this.$listeners,
        // Override input listener to work with v-model
        input: event => this.$emit('input', event.target.value)
      }
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.input {
  width: 300px;
  padding: 8px 10px;
  border: 1px solid $vue-blue;
}
</style>

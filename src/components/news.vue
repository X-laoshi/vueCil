<template>
	<li>
	{{ todo.text }}
	<button @click="$emit('remove', todo.id)" style="margin-left: 1.25rem;color: red;">
	finish
	</button>
	</li>
</template>

<script>
export default {
	props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
</style>

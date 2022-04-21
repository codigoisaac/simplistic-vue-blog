<template>
  <h3>{{ post.title }}</h3>
  <p>{{ snippet }}</p>
  <span v-for="tag in post.tags" :key="tag"> #{{ tag }}</span>
</template>

<script>
import { computed } from 'vue'

export default {
  props: ['post'],

  setup(props) {
    const snippet = computed(() => {
      return props.post.body.substr(0, 100) + '...'
    })

    return { snippet }
  },
}
</script>

<style></style>

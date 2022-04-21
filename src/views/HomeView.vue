<template>
  <div class="home">
    <input type="text" v-model="search" />

    <p>search term: {{ search }}</p>

    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
  </div>
</template>

<script>
import { computed, ref } from 'vue'

export default {
  name: 'HomeView',

  setup() {
    const names = ref([
      'thierre',
      'rhamys',
      'isaac',
      'atos',
      'jéssica',
      'abner',
    ])
    const search = ref('')

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    return { names, search, matchingNames }
  },
}
</script>

<template>
  <div class="home">
    <input type="text" v-model="search" />

    <p>search term: {{ search }}</p>

    <div v-for="name in matchingNames" :key="name">{{ name }}</div>

    <button @click="handleClick">Stop watching</button>
  </div>
</template>

<script>
import { computed, ref, watch, watchEffect } from 'vue'

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

    const stopWatchingSearch = watch(search, () => {
      console.log('search changed:', search.value)
    })

    const stopWatchEffect = watchEffect(() => {
      console.log('watchEffect ran:', search.value)
    })

    const handleClick = () => {
      stopWatchingSearch()
      stopWatchEffect()
    }

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    return { names, search, matchingNames, handleClick }
  },
}
</script>

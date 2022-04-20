<template>
  <div class="home">
    <p ref="p">
      We did it, Vue. My name is {{ name }} and my light is {{ light }}+.
    </p>

    <button @click="handleClick">Ye</button>
    <button @click="light++">+</button>

    <input type="text" v-model="name" />
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'

export default {
  name: 'HomeView',

  setup() {
    const name = ref('Isaac')
    const light = ref(99)

    const p = ref(null)

    const handleClick = () => {
      p.value.textContent = 'Ye'
      name.value = name.value + ':)'
    }

    return { name, light, handleClick, p }
  },
}
</script>

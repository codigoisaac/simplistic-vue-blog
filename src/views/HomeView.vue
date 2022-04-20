<template>
  <div class="home">
    <p ref="p">
      We did it, Vue. My name is {{ name }} and my light is {{ light }}.
    </p>

    <button @click="handleClick">Ye</button>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
  name: 'HomeView',

  setup() {
    const name = 'Isaac'
    const light = '99+'

    const p = ref(null)

    const handleClick = () => {
      p.value.textContent = 'Ye'
    }

    return { name, light, handleClick, p }
  },
}
</script>

<template>
  <div class="home">
    <div v-if="error">{{ error }}</div>

    <h1>Home</h1>

    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import { ref } from 'vue'
import PostList from '../components/PostList.vue'

export default {
  name: 'HomeView',
  components: { PostList },

  setup() {
    const posts = ref([])
    const error = ref(null)

    const load = async () => {
      try {
        const data = await fetch('http://localhost:3000/posts')

        if (!data.ok) {
          throw Error('No data available')
        }

        posts.value = await data.json()
      } catch (err) {
        error.value = err.message
        console.log(error.value)
      }
    }

    load()

    return { posts, error }
  },
}
</script>

<template>
  <div class="home">
    <h1>Home</h1>

    <PostList :posts="posts" />
  </div>
</template>

<script>
import { ref } from 'vue'
import PostList from '../components/PostList.vue'

export default {
  name: 'HomeView',
  components: { PostList },

  setup() {
    const posts = ref([
      { title: 'welcome to the blog', body: 'Lorem ipsum', id: 1 },
      { title: 'welcome again to the blog', body: 'Lorem again ipsum', id: 2 },
    ])

    return { posts }
  },
}
</script>

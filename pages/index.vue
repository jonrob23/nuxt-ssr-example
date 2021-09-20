<template>
  <div class="home-page">
    <b-container>
      <b-row class="mt-4">
        <b-col md="8" offset-md="2">
          <b-card
            v-for="post in posts"
            :key="post.id"
            :img-src="`https://picsum.photos/600/300/?image=${post.id}`"
            img-alt="Image"
            img-top
            tag="article"
            class="shadow border-0 mb-4"
          >
            <nuxt-link :to="{ name: 'id', params: { id: post.id } }" class="text-dark">
              <b-card-title class="text-capitalize">{{ post.title }}</b-card-title>
            </nuxt-link>
            <b-card-text>
              {{ post.body }}
            </b-card-text>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const posts = await $axios.$get(
      'https://jsonplaceholder.typicode.com/posts'
    )
    return { posts }
  },

  data() {
    return {
      posts: [],
    }
  },
}
</script>

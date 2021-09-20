<template>
  <div class="post-page">
    <b-container>
      <b-row class="mt-4">
        <b-col md="8" offset-md="2">
          <b-button to="/" variant="outline-primary" class="px-4 mb-3" pill>
            Go back
          </b-button>

          <b-card
            :img-src="`https://picsum.photos/600/300/?image=${post.id}`"
            img-alt="Image"
            img-top
            tag="article"
            class="shadow border-0"
          >
            <b-card-title class="text-capitalize">{{ post.title }}</b-card-title>
            <b-card-text>
              {{ post.body }}
            </b-card-text>
            <p v-for="num in 5" :key="num">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempore
              officia, aperiam sunt illo itaque unde assumenda, placeat neque
              quidem porro nobis voluptate, facilis repellendus quasi soluta.
              Deleniti consectetur deserunt minus?
            </p>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    const post = await $axios.$get(
      `https://jsonplaceholder.typicode.com/posts/${params.id}`
    )
    return { post }
  },

  data() {
    return {
      post: [],
    }
  },
}
</script>

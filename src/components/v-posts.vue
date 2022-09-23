<template>
  <div class="v-posts">
    <div class="v-posts__container">
      <div class="v-posts__wrapper">
        <v-post
            v-for="post in filteredPosts"
            :key="post.id"
            :post="post"
        >
        </v-post>
      </div>
    </div>
  </div>
</template>

<script>
import VPost from "@/components/v-post";

export default {
  name: "v-posts",
  components: {VPost},
  props: {
    filteredPosts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss">
.v-posts {
  margin-top: 15px;

  &__wrapper{
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  &__container {
    max-width: 1405px;
    margin: 0 auto;
    box-sizing: content-box;
    padding: 0 30px;
  }
}

</style>
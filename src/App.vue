<template>
  <div class="app">
    <div class="search-post">
      <div class="search-post__icon" >
        <img src="./img/search.svg" alt="Search">
      </div>
      <v-input placeholder="Filter by author..."
               v-model="searchQuery"
               @input="searchPost"
      >
      </v-input>
    </div>
    <v-posts
        :filteredPosts="filteredPosts"
        v-if="!isPostsLoading"
    />
    <div v-else class="loading-posts">Идет загрузка...</div>
  </div>
</template>

<script>

import VPosts from "@/components/v-posts";
import axios from 'axios';
import VInput from "@/components/UI/v-input";

export default {
  name: 'App',
  components: {VInput, VPosts},
  data() {
    return {
      posts: [],
      filteredPosts: [],
      isPostsLoading: false,
      searchQuery: ''
    }
  },
  methods: {
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        let response = await axios.get('http://jsonplaceholder.typicode.com/posts?_limit=20');
        this.posts = response.data;
        response = await axios.get('http://jsonplaceholder.typicode.com/users?_limit=20');
        this.users = response.data;

        this.posts.forEach((post) => {
          let user = this.users.find((user) => {
            return user.id === post.userId;
          })
          post.userName = user.name;
        })

        this.filteredPosts = this.posts;

        this.isPostsLoading = false;
      } catch (e) {
        alert('Error!')
      } finally {
        this.isPostsLoading = false;
      }
    },
    searchPost(){
      this.filteredPosts = this.posts.filter(post => post.userName.includes(this.searchQuery))
    }
  },

  mounted() {
    this.fetchPosts();

  }
}
</script>

<style lang="scss">
@import '~@/assets/styles/styles.scss';
@import '~bootstrap/dist/css/bootstrap.css';
.search-post{
  display: flex;
  justify-content: center;
  align-items: baseline;
  padding: 0 15px;

  &__icon{
    box-shadow: 0 5px 5px 5px rgba(34, 60, 80, 0.05);
    -webkit-box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
    -moz-box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
    background-color: #ffffff;
    padding: 0 7px;
    border-radius: 5px 0 0 5px;
    border-right: 1px solid #9c9c9c;
  }

  &__icon img{
    width: 20px;
  }
}

img, svg {
  vertical-align: text-bottom!important;
}
</style>

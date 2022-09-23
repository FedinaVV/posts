<template>
  <div class="v-post col-xl-3 col-lg-4 col-md-4 col-sm-10 col-xs-10">
    <div class="v-post__title">{{ post.title }}</div>
    <div class="v-post__body">{{ post.body }}</div>
    <div class="v-post__author">{{ post.userName }}</div>
  </div>
</template>

<script>

export default {
  name: "v-post",
  data() {
  },
  props: {
    post: {
      type: Object,
      required: true
    }
  },
  methods: {
  },
}
</script>

<style scoped lang="scss">
.v-post {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: #ffffff;
  box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
  -webkit-box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
  -moz-box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
  border-radius: 5px;
  padding: 15px;
  margin: 15px 15px;

  &__title {
    font-size: 18px;
    color: #75aae9;
    font-weight: 600;
    margin-bottom: 10px;
  }

  &__body {
    font-size: 14px;
    margin-bottom: 10px;
  }

  &__author {
    font-size: 12px;
    opacity: 0.5;
  }
}
</style>
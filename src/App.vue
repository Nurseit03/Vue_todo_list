<template>
  <div class="app">
    <post-form @create="createPost" />
    <post-list :posts="posts" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
export default {
  components: {
    PostList,
    PostForm,
  },
  data() {
    return {
      posts: [
        // { id: 1, title: "Пост", body: "тело поста 1" },
        // { id: 2, title: "Пост2", body: "тело поста 2" },
        // { id: 3, title: "Пост3", body: "тело поста 3" },
      ],
      title: "",
      body: "",
    };
  },
  methods: {
    createPost(post) {
      if (post.title.trim() === "" || post.body.trim() === "") {
        return;
      }
      this.posts.push(post);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>

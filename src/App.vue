<template>
  <div class="app">
    <post-form @create="createPost" />
    <post-list :posts="posts" @remove="removePost" @edit="editPost"/>
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
      posts: JSON.parse(localStorage.getItem("posts")) || [],
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
      this.savePostsToLocalStorage();
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
      this.savePostsToLocalStorage();
    },
    savePostsToLocalStorage() {
      localStorage.setItem("posts", JSON.stringify(this.posts));
    },
    editPost(post) {
        
    }
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

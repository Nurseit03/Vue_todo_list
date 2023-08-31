<template>
  <form @submit.prevent>
    <h4>{{ editing ? "Редактирование поста" : "Создание поста" }}</h4>
    <my-input v-model.trim="post.title" type="text" placeholder="Название" />
    <my-input v-model.trim="post.body" type="text" placeholder="Описание" />
    <my-button
      @click="editing ? editPost() : createPost()"
      style="align-self: flex-end; margin-top: 15px"
    >
      {{ editing ? "Сохранить" : "Создать" }}
    </my-button>
  </form>
</template>

<script>
export default {
  props: {
    editing: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      if (this.post.title.trim() === "" || this.post.body.trim() === "") {
        return;
      }
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
    editPost() {
      if (this.post.title.trim() === "" || this.post.body.trim() === "") {
        return;
      }
      this.$emit("edit", this.post);
      this.post = {
        title: "",
        body: "",
      };
      
      this.$emit("close-dialog");
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
}
</style>

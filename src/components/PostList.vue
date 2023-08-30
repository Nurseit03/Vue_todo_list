<template>
  <div>
    <h4>{{ posts.length > 0 ? 'Список постов' : 'Список постов пуст' }}</h4>
    <post-item 
    v-for="post in posts" 
    :post="post" 
    :key="post.id"
    @remove="$emit('remove', post)"
    @edit="$emit('edit', post)"
    />
  </div>
</template>

<script>
import PostItem from "@/components/PostItem.vue";
export default {
  components: {
    PostItem,
  },
  props: {
    posts: {
      type: Array,
      require: true,
    },
  },
};
</script>

<style scoped></style>

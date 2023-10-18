<template>
   <div v-if="posts.length">
      <h1>Список пользователей</h1>
      <post-item 
        v-for="post of posts"
        :key="post.id"
        :post="post"
        @remove="this.$emit('remove', post)"
      />
   </div>
   <h1 v-else>Постов нет</h1>
</template>

<script>
import PostItem from './PostItem.vue'
export default {
  props: {
    posts: {
      type: Array,
      required: true
    }
  },
  components: {
    PostItem
  }
}
</script>

<style scoped>

</style>

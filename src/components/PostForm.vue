<template>
  <form @submit.prevent="createPost">
    <input 
      type="text"
      v-model="post.title"
      placeholder="Название"
    />
    <input 
      type="text"
      v-model="post.body"
      placeholder="Заголовок"
    />
    <button
      class="btn"
      type="submit"
    >
      add post
    </button>
  </form>
</template>

<script>
export default {
  name: 'postForm',
  data() {
    return {
      post: {
        title: "",
        body: "",
      }
    }
  },
  methods: {
    createPost() {
      const newPost = {
        id: new Date(),
        ...this.post
      }
      this.$emit('create', newPost);
      this.post = {
        title: "",
        body: "",
      }
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

input {
  padding: 20px;
  border: 1px solid goldenrod;
  border-radius: 3px;
  font-size: 18px;
}
.btn {
  padding: 10px 20px;
  border: none;
  background: rgb(241, 148, 148);
  color: white;
  font-size: 26px;
  cursor: pointer;
}
</style>

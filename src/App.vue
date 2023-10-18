<template>
  <div class="app">
    <button class="btn-create" @click="showModal">Создать пользователя</button>
    <my-select
      v-model="selectedSort"
      :options="sortOptions"
    />
    <my-modal v-model:show="show">
      <post-form
        @create="createPost"
      />
    </my-modal>
    <post-list
      v-if="!isPostLoading"
      :posts="posts"
      @remove="removePost"
    />
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostForm from '@/components/PostForm.vue'
import PostList from '@/components/PostList.vue'
import MyModal from '@/components/UI/MyModal.vue'
import axios from 'axios'
import MySelect from './components/UI/MySelect.vue'

export default {
  name: 'app',
  components: {
    PostForm,
    PostList,
    MyModal,
    MySelect,
  },
  data() {
    return {
      selectedSort: '',
      sortOptions: [
        { value: "title", name: 'По названию' },
        { value: "body", name: 'По описанию' }
      ],
      show: false,
      posts: [],
      isPostLoading: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.show = false;
    },
    removePost({id}) {
      this.posts = this.posts.filter(p => p.id !== id);
    },
    showModal() {
      this.show = true;
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true;
        const { data } = await axios('https://jsonplaceholder.typicode.com/posts?_limit=10');
        this.posts = data;
      } catch(e) {
        console.log(e);
      } finally {
        this.isPostLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPosts();
  }
}
</script>

<style scoped>
.app {
  max-width: 600px;
  margin: 0 auto;
}

.btn-create {
  padding: 8px;
  background: none;
  border-radius: 6px;
  margin: 0 auto;
}
</style>

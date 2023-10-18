<template>
  <div class="post">
    <div>
      <div><strong>Название:</strong> {{ post.title }}</div>
      <div><strong>Описание:</strong> {{ post.body }}</div>
    </div>
    <div class="btns">
      <button class="btn-remove" @click="this.$emit('remove', post)">delete</button>
      <button class="btn-change">change</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.post {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 40px 0;
  border: 1px solid goldenrod;
  padding: 20px;
  border-radius: 3px;
}
.btn-remove {
  color: white;
  background: red;
  padding: 10px;
  border-radius: 6px;
  cursor: pointer;
}

.btn-change {
  background: rgb(255, 246, 87);
  padding: 10px;
  border-radius: 6px;
  cursor: pointer;
}
</style>

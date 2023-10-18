<template>
  <div v-if="show" class="modal" @click.stop="toggleModal">
    <div @click.stop class="modal__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'modal',
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    toggleModal() {
      this.$emit('update:show', false);
    }
  }
}
</script>

<style scoped>
.modal {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.3);
}

.modal__content {
  max-width: 620px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 8px;
  background: white;
}
</style>

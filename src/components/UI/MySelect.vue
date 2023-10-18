<template>
  <select :value="modelValue" @change="changeOptions">
    <option disabled value="">Выберите из списка</option>
    <option
      v-for="op in options"
      :key="op.value"
      :value="op.value"
    >
      {{ op.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'my-select',
  props: {
    modelValue: {
      type: String,
      default: '',
    },
    options: {
      type: Array,
      default: () => [],
    }
  },
  data() {
    return {

    }
  },
  methods: {
    changeOptions(e) {
      this.$emit('update:modelValue', e.target.value)
    }
  }
}
</script>
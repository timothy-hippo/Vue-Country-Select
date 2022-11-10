<template>
  <select class="form-select" v-model="index">
    <option selected disabled value="">請選擇縣市</option>
    <option v-for="(item,idx) in options" :key="idx" :value="idx">{{item}}</option>
  </select>
</template>

<script>
export default {
  props: ['modelValue', 'options'],
  data () {
    return {}
  },
  computed: {
    index: {
      get () {
        return this.modelValue
      },
      set (val) {
        this.$emit('update:modelValue', val)
      }
    }
  }
}
</script>

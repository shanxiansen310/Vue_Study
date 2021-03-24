<template>
  <li @click="handleDelete">{{ content }}</li>
</template>

<script>
export default {
  props: ['content', 'index'], // 父组件借此向子组件传值
  methods: {
    handleDelete: function () {
      this.$emit('delete', this.index) // 抛出一个事件,让父组件定义
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

<template>
  <div class="post">
    <div><b>Name: </b>{{ post.title }}</div>
    <div><b>Description: </b>{{ post.body }}</div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style scoped>

</style>
<template>
  <div class="post">
    <div>
      <div><b>ID: </b>{{ post.id }}</div>
      <div><b>Name: </b>{{ post.title }}</div>
      <div><b>Description: </b>{{ post.body }}</div>
    </div>
    <div class="post__buttons">
      <my-button @click="$router.push(`/posts/${post.id}`)">Open</my-button>
      <my-button @click="$emit('remove', post)">Remove</my-button>
    </div>
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
.post {
  padding: 15px;
  border: 2px solid gold;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.post__buttons {
  display: flex;
}
</style>
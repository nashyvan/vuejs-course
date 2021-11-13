<template>
  <div class="app">
    <h1>Page with posts</h1>
    <my-button class="my-15px" @click="showDialog">Create post</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"/>
    </my-dialog>
    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
  components: {
    PostForm, PostList,
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'Description'},
        {id: 2, title: 'JavaScript 2', body: 'Description 2'},
        {id: 3, title: 'JavaScript 3', body: 'Description 3'},
        {id: 4, title: 'JavaScript 4', body: 'Description 4'},
      ],
      dialogVisible: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(p =>p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    },
  }
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

.self-end {
  align-self: flex-end;
}

.mt-15px {
  margin-top: 15px;
}

.my-15px {
  margin-top: 15px;
  margin-bottom: 15px;
}

</style>
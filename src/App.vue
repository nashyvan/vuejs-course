<template>
  <div class="app">
    <h1>Page with posts</h1>
    <div class="app__buttons">
      <my-button class="my-15px" @click="showDialog">Create post</my-button>
      <my-select :options="sortOptions" v-model="selectedSort"/>
    </div>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"/>
    </my-dialog>
    <post-list :posts="sortedPosts" @remove="removePost" v-if="!isPostsLoading" />
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import axios from 'axios'

import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import MyButton from "./components/UI/MyButton";
import MySelect from "./components/UI/MySelect";

export default {
  components: {
    PostForm, PostList, MyButton, MySelect
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort: '',
      sortOptions: [
        { value: 'title', name: 'Sort by title' },
        { value: 'body', name: 'Sort by body' },
      ]
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
    async fetchPosts() {
      try {
        this.isPostsLoading = true
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = response.data
      } catch (e) {
        alert('Error')
      } finally {
        this.isPostsLoading = false
      }
    }
  },
  mounted() {
    this.fetchPosts()
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
    },
  },
  // watch: {
  //   selectedSort(newValue) {
  //     this.posts.sort((post1, post2) => {
  //       return post1[newValue]?.localeCompare(post2[newValue])
  //     })
  //   }
  // }
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

.app__buttons {
  display: flex;
  justify-content: space-between;
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
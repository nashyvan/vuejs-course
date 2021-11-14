<template>
  <div class="navbar">
    <div @click="$router.push('/')">Vue 3</div>
    <div class="navbar__buttons">
      <my-button @click="$router.push('/posts/')">Posts</my-button>
      <my-button @click="$router.push('/about/')" class="ml-15px">About</my-button>
<!--      <my-button @click="$router.push('/store/')" class="ml-15px">store</my-button>-->
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.navbar {
  display: flex;
  background: lightgray;
  height: 50px;
  box-shadow: 2px 2px 4px gray;
  align-items: center;
  padding: 0 15px;
}

.navbar__buttons {
  margin-left: auto;
}
</style>
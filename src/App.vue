<template>
  <navbar></navbar>
  <div class="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
export default {
  components: {
    Navbar,
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

.ml-15px {
  margin-left: 15px;
}

.my-15px {
  margin-top: 15px;
  margin-bottom: 15px;
}


</style>
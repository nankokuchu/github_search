<template>
  <section class="jumbotron">
    <h3 class="jumbotron-heading">Search Github Users</h3>
    <div>
      <input type="text" placeholder="enter the name you search" v-model="keyWord"/>&nbsp;
      <button @click="searchUsers">Search</button>
    </div>
  </section>
</template>

<script>
import axios from 'axios'

export default {
  name: "KeySearch",
  data() {
    return {
      //数据
      keyWord: ''
    }
  },
  methods: {
    searchUsers() {
      // ajax 请求发送之前
      this.$bus.$emit('updateUserList', {isFirst: false, isLoading: true, errMsg: '', users: []})
      axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
          response => {
            this.$bus.$emit('updateUserList', {isLoading: false, errMsg: '', users: response.data.items});
          },
          error => {
            this.$bus.$emit('updateUserList', {isLoading: false, errMsg: error.message, users: []});
          }
      )
    }
  }
}
</script>

<style scoped>

</style>
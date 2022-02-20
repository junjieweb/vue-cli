<template>
  <div class="row">
    <h2 v-if="isFirst">欢迎使用</h2>
    <h2 v-else-if="isLoading">搜索中ing</h2>
    <h2 v-else-if="error">请求失败了：{{ error }}</h2>
    <div v-else class="card" v-for="(user) in users" :key="user.username">
      <a :href="user.userurl" target="_blank">
        <img :src="user.userimg" style='width: 100px' alt="头像"/>
      </a>
      <p class="card-text">{{ user.username }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: "Main",
  data() {
    return {
      isFirst: true,
      isLoading: false,
      error: '',
      users: []
    }
  },
  mounted() {
    this.$bus.$on('searchAjax',this.searchAjax)
  },
  methods: {
    searchAjax(q) {
      this.isFirst = false
      this.isLoading = true
      axios({
        url: 'https://api.github.com/search/users',
        method: 'get',
        params: {
          q
        }
      }).then(response => {
        this.isLoading = false
        this.users = response.data.items.map(item => ({
          username: item.login,
          userurl: item.html_url,
          userimg: item.avatar_url
        }))
      }).catch(error => {
        this.isLoading = false
        this.error = error.message
      })
    }
  }
}
</script>

<style scoped>
.card {
  float: left;
  width: 33.333%;
  padding: .75rem;
  margin-bottom: 2rem;
  border: 1px solid #efefef;
  text-align: center;
}

.card > img {
  margin-bottom: .75rem;
  border-radius: 100px;
}

.card-text {
  font-size: 85%;
}
</style>
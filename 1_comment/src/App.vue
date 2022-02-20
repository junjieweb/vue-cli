<template>
  <div>
    <Header></Header>
    <div class="container">
      <Add @addComment="addComment"></Add>
      <List :comments="comments" :deleteContent="deleteContent"></List>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Add from "@/components/Add";
import List from '@/components/List';

export default {
  name: "App",
  components: {
    Header,
    Add,
    List
  },
  data() {
    return {
      comments: [
        {id: 1, content: 'vue好用', username: '刘德华'},
        {id: 2, content: 'vue不错哦', username: '周杰伦'},
        {id: 3, content: 'vue好难啊', username: '洛丽塔'}
      ]
    }
  },
  methods: {
    addComment(comment) {
      this.comments.unshift(comment)
    },
    deleteContent(index) {
      this.comments.splice(index, 1)
    }
  }
};
</script>

<style scoped>

</style>

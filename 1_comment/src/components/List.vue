<template>
  <div class="col-md-8">
    <h3 class="reply">评论回复：</h3>
    <h2 style="display: none">暂无评论，点击左侧添加评论！！！</h2>
    <ul class="list-group">
      <Item
        v-for="(comment,index) in comments"
        :key="comment.id"
        :comment="comment"
        :index="index"
        :deleteContent="deleteContent"
      ></Item>
    </ul>
  </div>
</template>

<script>
import Item from '@/components/Item';
export default {
  name: "List",
  components:{Item},
  props:['comments','deleteContent'],
};
</script>

<style scoped>
.reply {
  margin-top: 0;
}
</style>
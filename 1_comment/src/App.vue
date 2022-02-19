<template>
  <div>
    <Header></Header>
    <div class="container">
      <Add></Add>
      <List></List>
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
};
</script>

<style>
.reply {
  margin-top: 0;
}

li {
  transition: 0.5s;
  overflow: hidden;
}

.handle {
  width: 40px;
  border: 1px solid #ccc;
  background: #fff;
  position: absolute;
  right: 10px;
  top: 1px;
  text-align: center;
}

.handle a {
  display: block;
  text-decoration: none;
}

.list-group-item .centence {
  padding: 0px 50px;
}

.user {
  font-size: 22px;
}
</style>

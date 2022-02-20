<template>
  <li @mouseenter="isShow = true" @mouseleave="isShow = false" :class="{show:isShow}">
    <label>
      <input type="checkbox" v-model="todo.isOver" @click="updateO" :checked="todo.isOver"/>
      <span>{{ todo.content }}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="deleteO">删除</button>
  </li>
</template>

<script>
export default {
  name: "Item",
  props: {
    todo: Object,
    index: Number
  },
  data() {
    return {
      isShow: false
    }
  },
  methods: {
    updateO() {
      this.$emit('updateOne', this.index)
    },
    deleteO() {
      if (confirm('确定删除吗？')) {
        this.$bus.$emit('deleteOne', this.index)
      }
    }
  }
}
</script>

<style scoped>
.show {
  background: #f58989;
}

/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>
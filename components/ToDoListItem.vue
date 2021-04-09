<template>
  <div class="to-do-item" :class="{ completed: todo.completed }">
    <span>{{ todo.title }}</span>
    <div class="controls">
      <span @click="deleteItem">❌</span>
      <span @click="completeItem">✅</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  methods: {
    completeItem() {
      this.todo.completed = true
    },
    deleteItem() {
      this.$emit('delete', this.todo)
    },
  },
}
</script>

<style>
.to-do-item {
  width: 100%;
  display: block;
  height: 50px;
  border-top: solid 1px #eeeeee;
  font-size: 24px;
}
.completed {
  opacity: 0.4;
}
.to-do-item span {
  height: 50px;
  padding-left: 20px;
  line-height: 50px;
  width: 450px;
  text-align: left;
  display: inline-block;
}
.to-do-item .controls {
  display: inline-block;
  height: 50px;
  line-height: 50px;
  float: right;
}
.to-do-item .controls span {
  line-height: 50px;
  height: 50px;
  display: inline-block;
  width: 45px;
  text-align: center;
  padding: 0;
  cursor: pointer;
}
</style>

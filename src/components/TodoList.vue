<template>
  <div class="todo">
    <h1>Todo App</h1>

    <input
      class="name"
      type="text"
      placeholder="Enter Your todo"
      name="todo"
      v-model="string"
      required
    />

    <button v-on:click="todo0()" id="btn">+</button>

    <p>List Is:{{ todo }}</p>
  </div>
</template>
<script>
export default {
  name: "TodoList",
  data() {
    return {
      todo: [],
      string: " ",
    };
  },
  methods: {
    todo0() {
      this.todo.push(this.string);

      this.string = "";
    },
  },
};
</script>
<style>
.todo {
  margin: 10%;
  padding: 10%;
  border: 3px solid;
}

#btn {
  margin: 10px;
  padding: 10px;
  color: crimson;
  cursor: pointer;
  font-size: 20px;
  font-weight: 400;
}

.name {
  width: 500px;
  height: 30px;
  margin-bottom: 20px;
}
</style>

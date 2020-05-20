<template>
  <div class = "todo-item" v-bind:class="{'is-complete': todo.completed}">
      <p> 
        <input type="checkbox" v-on:change="markComplete">
        {{todo.title}}
        <button @click= "$emit('del-todo', todo.id)"
         class = "del"> X </button>
    </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        /* Adds a method to functionality of Todo Item and checks off todo
        *   when you click the checkbox button
        */ 
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: #eedf09ef;
        padding: 30px;
        border-bottom: 5px #ccc dashed;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 6px 8px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>
<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbos" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
            </p>
    </div>
</template>


<script>
export default {
    name: 'TodoItems',
    props: ["todo"],
    methods: {
        markComplete () {
        this.completed = !this.completed;
        }
        }
}
</script>

<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px solid 
    }

    .is-complete {
        text-decoration: line-through;
         }

    .del {
        background: #ffff00
    }
</style>
<template>
    <div class="todo-item">
        <p>{{todo.title}}</p>
    </div>
</template>


<script>
export default {
    name: 'ItemsDo',
    props: ["todo"]
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
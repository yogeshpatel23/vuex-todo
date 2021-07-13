<template>
    <div>
        <h3>Todos</h3>
        <div class="todos">
            <div @dblclick="onDblClick(todo)" v-for="todo in allTodos" :key="todo.id" :class="[ todo.completed ? 'is-comleted' : '' ,'todo']">
                <i @click="deleteTodo(todo.id)" class="fas fa-times"></i>
                <h4>{{ todo.title }}</h4>
            </div>
        </div>
    </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
    name: 'Todos',
    computed: mapGetters(['allTodos']),
    methods: {
        ...mapActions(['fetchTodos','deleteTodo','updateTodo']),
        onDblClick(todo){
            const updTodo = { ...todo, completed: !todo.completed }
            this.updateTodo(updTodo)
        }
    },
    created() {
        this.fetchTodos()
    }
}
</script>

<style scoped>
.todos {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
    gap: 1rem;
}

.todo {
    border: 1px solid #ccc;
    background: #51ca75;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer;
}

.is-comleted {
    background: darkgray;
}

.todo .fas {
    position: absolute;
    top: 10px;
    right: 10px;
    color: red;
}
</style>
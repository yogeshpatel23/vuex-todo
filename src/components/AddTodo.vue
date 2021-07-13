<template>
    <div>
        <h3>Add Todo</h3>
        <div class="add">
            <form @submit="onSubmit">
                <input type="text" v-model="title" placeholder="Add Todo">
                <input type="submit" value="Save" class="btn">
            </form>
        </div>
    </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
    name: 'AddTodo',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        ...mapActions(['addTodo']),
        onSubmit(e) {
            e.preventDefault()

            if (!this.title) {
                alert('Please Enter Todo');
                return
            }

            this.addTodo(this.title)
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
}

input[type='text'] {
    flex: 10;
    padding: 10px;
    border: 1px solid #41b883;
    border-radius: 10px 0 0 10px;
    outline: none;
}

input[type='submit'] {
    flex: 2;
    background: #41b886;
    color: #fff;
    border: 1px solid #41b883;
    cursor: pointer;
    border-radius: 0 10px 10px 0;
}
</style>
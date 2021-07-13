<template>
    <div class="filter">
        Filter Todos :
        <select @change="filterTodos($event)">
            <option value="200">200</option>
            <option value="100">100</option>
            <option value="50">50</option>
            <option value="10">10</option>
            <option value="5">5</option>
        </select>
    </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
    name: 'FilterTodos',
    methods: mapActions(['filterTodos'])
}
</script>

<style scoped>
.filter {
    margin-top: 20px;
}

select {
    width: 100px;
    padding: 5px;
    border: none;
    border-bottom: 2px solid #41b883;
    font-size: 16px;
}
</style>
<template>
    <!-- maybe is-mobile as well if u wana test on phone and 
        is-multiline makes it so children -->
    <div class="columns is-multiline is-centered">
        <!-- 1st column | Input todo -->
        <div class="column has-text-centered">
            <form @submit.prevent="addTodo">
                <input v-model="text" @keydown.enter="preventEnter" placeholder="Enter Todo Item"/>
                    <button>Add todo</button>
            </form>
            <!-- <p> {{ text }}</p>      -->
        </div>
            <!-- is-full creates newline cuz takes up width of container -->
            <div class="column has-text-centered is-full"> 
                <div class="column ">
                <ul>
                    <li v-for="todo in todos" :key="todo.id">
                        <!-- current todo is passed into function if removal is wanted -->
                        {{ todo.text }} <button @click="removeTodo(todo)">X</button>
                    </li>
                </ul>
            </div>
        </div>
    </div>

</template>

<script setup>
import { ref } from 'vue'

const text = ref('')
let id = 0
const todos = ref([

    {id: id++, text: 'Todo Placeholder!', done: false},
    {id: id++, text: 'Remove Me!', done: false},
    {id: id++, text: 'Add another one!', done: false}
])

function addTodo(){
    if (text.value.trim() !== ''){
        todos.value.push({id: id++, text: text.value})
        text.value = ''
    }
}

function removeTodo(todo){
    // remove object from todos array
    todos.value = todos.value.filter((ele) => ele.id !== todo.id)
}

// when enter key is pressed in input field, event 
// handler is triggered, and the event object is automatically
//  passed as an argument to function below
function preventEnter(event){
    event.preventDefault()
}

</script>

<style scoped>

    ul{
        list-style-type: none;
    }

</style>
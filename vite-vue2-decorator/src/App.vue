<template>
    <div>
        <h1>My ToDo</h1>
        <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add todo..." />
        <ul>
            <TodoItem v-for="(todo, index) in todos" :key="index" :text="todo" @remove="removeTodo(index)" />
        </ul>
    </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import TodoItem from './components/TodoItem.vue';

@Component({
    components: { TodoItem }
})
export default class App extends Vue {
    newTodo: string = '';
    todos: string[] = [];

    addTodo() {
        if (this.newTodo.trim()) {
            this.todos.push(this.newTodo.trim());
            this.newTodo = '';
        }
    }

    removeTodo(index: number) {
        this.todos.splice(index, 1);
    }
}
</script>

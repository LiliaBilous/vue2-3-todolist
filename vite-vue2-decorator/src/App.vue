<template>
    <div class="wrapper">
        <div class="main">
            <h1 class="main__title">My ToDo List</h1>
            <TodoList></TodoList>
        </div>
        <AppFooter></AppFooter>
    </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import TodoList from '@/components/TodoList.vue';
import AppFooter from '@/AppFooter.vue';

@Component({
    components: { TodoList, AppFooter }
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

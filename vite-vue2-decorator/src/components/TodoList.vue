<template>
    <div class="todo-list__wrapper">
        <div class="toolbar__wrapper">
            <TodoVisibilityToggle></TodoVisibilityToggle>
            <TodoFilters></TodoFilters>
        </div>
        <TodoInput @add="addTodo" />
        <div class="list__wrapper">
            <ul>
                <TodoItem v-for="(todo, index) in todos" :key="index" :text="todo" @remove="removeTodo(index)" />
            </ul>
        </div>
    </div>

</template>
<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import TodoInput from "@/components/TodoInput.vue";
import TodoVisibilityToggle from "@/components/TodoVisibilityToggle.vue";
import TodoFilters from "@/components/TodoFilters.vue";
import TodoItem from "@/components/TodoItem.vue";

@Component({
    components: { TodoInput, TodoVisibilityToggle, TodoFilters, TodoItem }
})
export default class TodoList extends Vue {
    todos: string[] = [];

    addTodo(todo: string) {
        this.todos.push(todo);
    }

    removeTodo(index: number) {
        this.todos.splice(index, 1);
    }
}
</script>
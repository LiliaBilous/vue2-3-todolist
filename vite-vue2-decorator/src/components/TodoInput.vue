<template>
    <div class="input__wrap">
        <input v-model="newTodo" @keyup.enter="submitTodo" placeholder="Add todo item..." />
    </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component
export default class TodoInput extends Vue {
    newTodo: string = '';

    submitTodo() {
        if (this.newTodo.trim()) {
            this.$emit('add', this.newTodo);
            this.newTodo = '';
        }
    }
}
</script>

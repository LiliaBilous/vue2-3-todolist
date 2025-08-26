<template>
    <li>
        <input type="checkbox" v-model="done" />
        <span :class="{ completed: done }">{{ capitalizedText }}</span>
        <button @click="remove">x</button>
    </li>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component
export default class TodoItem extends Vue {
    // Props
    @Prop({ type: String, required: true }) readonly text!: string;

    // Data
    done: boolean = false;

    // Computed
    get capitalizedText(): string {
        return this.text.charAt(0).toUpperCase() + this.text.slice(1);
    }

    // Methods
    remove() {
        this.$emit('remove');
    }
}
</script>

<style scoped>
.completed {
    text-decoration: line-through;
}
</style>

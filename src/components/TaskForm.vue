<template>
    <form @submit.prevent="CreateTask">
        <input 
        v-model="task.title"
        class="InputCreate" 
        type="text"
        placeholder="Ваша задача">
        <button type="submit" class="ButtonCreate" @click="CreateTask">Создать</button>
    </form>
</template>
<script>
export default {
    data() {
        return {
            task: {
                title: '',
            }
        }
    },
    methods: {
        CreateTask() {
            if (!this.task.title.trim()) {
                return;
            }
            this.task.id = Date.now();
            this.$emit('create', this.task);
            this.task = {
                title: ''
            };
        },
    }
}
</script>
<style scoped>
form {
    display: flex;
    flex-direction: column;
}

.InputCreate {
    width: 100%;
    border: 1px solid teal;
    padding: 10px 15px;
    margin-top: 15px;
}

.ButtonCreate {
    margin-top: 15px;
    align-self: flex-end;
    padding: 10px 15px;
    background: none;
    color: teal;
    border: 1px solid teal;
    cursor: pointer;
}
</style>
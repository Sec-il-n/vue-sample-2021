<template>
    <header>
        <h1>{{ title }}</h1>
        <!-- 使用出来る型->Button.vue props -->
        <!-- <Button @toggle-add-task="$emit('toggle-add-task')" text="AddTask" color="green"/> -->
        <Button @btn-click="$emit('toggle-add-task')"
        :text="showAddTask ? 'Close' : 'AddTask'"
        :color="showAddTask ? 'red' : 'green'"/>
        <!-- <Button text="UpdateTask" color="blue"/> -->
    </header>
</template>
<script>
import Button from './Button'
// Headerをimportshita先で適用されるdefault
export default{
    name: 'Header',
    // props: ['title']
    props: {
        title: String,
        showAddTask: Boolean,
    },
    //register
    components: {
        Button,
    },
}
</script>
<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>
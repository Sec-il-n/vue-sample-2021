<template>
    <div :key="task.id" v-for="task in tasks">
        <!-- a↑taskをコンポーネントに →b. Task.vue template に移す-->
        <!-- <h3>{{task.text}}</h3> -->
       
        <!-- d. instead <h3>-->
            <!-- は）データはさらに上位のAppに存在するので$emit -->
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />

    </div>
    
    <!-- <Task /> -->
</template>
<script>
import Task from './Task'//c.
// ①propsをtemplateで使用する為
export default {
    name: 'Tasks',
    props: {
        tasks: Array,
    },
    components: {
        Task,
    },
    //は）$emit登録
    emits: ['delete-task', 'toggle-reminder'],
}
</script>
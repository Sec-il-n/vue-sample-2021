<template>
<!-- Ⓜ︎.textが使用出来る -->
    <!-- <div class="task" > -->
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']" >
        <h3>
            {{task.text}}
            <!-- い）-->
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
            <!-- <i @click="onDelete()" class="fas fa-times"></i> -->
        </h3>
        <p>{{task.day}}</p>
    </div>
    
</template>
<script>
export default {
    name: 'Task',
    props: {
        task: Object,
    },
    // methods: {
    //     onDelete(id) {
    //         // console.log(id) //動作確認
    //         this.$emit('delete-task', id)
    //         //ろ) データ$emit→次のレベルで使用されているTaskへ（Tasksでバインド）
    //     },
    // },
}
</script>
<style scoped>
.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.task.reminder {
    border-left: 5px solid green;
}
.fas{
    color: red;
}

</style>
<template>
    <!-- <button class="btn">AddTask</button> -->
    <button @click="onClick" :style="{ background: color }" class="btn">{{ text }}</button>
</template>
<script>

export default {
    //Header.vueでimport
    name: 'Button',
    props: {
        text: String,
        color: String,

    },
    methods: {
        
        onClick(){
            // console.log('click')
            // this.$emit('toggle-add-task')
            // ジェネリックで再利用可能にする
            this.$emit('btn-click')
        },
    },
}
</script>

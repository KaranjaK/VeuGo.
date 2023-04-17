<template>
    <button @click="onClick()" :style="{background: color}" class="btn">{{ text }}</button>
</template>

<script>

    export default{
        name: 'TaskButton',
        props: {
            text: String,
            color: String,
        },
        methods:{
            onClick(){
                
            },
        }
    }
</script>
<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">clear all</span>
    </div>
</template>

<script>
    export default{
        methods:{
            clearTodo(){
                localStorage.clear();
            }
        }
    }
</script>

<style scoped>
    .clearAllContainer {width:80%;height:40px;line-height:40px;background:#fff;border-radius:20px;margin:0 auto;margin-top:30px}
    .clearAllBtn{color:#002346;display:block;font-size:1rem;font-weight:600;font-family:'Ubuntu', sans-serif;}
</style>
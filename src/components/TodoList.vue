<template>
    <section>
        <ul>
            <li v-for="(todoItem, index) in todoItems" :key="todoItem" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
    export default{
        data(){
            return{
                todoItems:[]
            }
        },
        created(){
            if(localStorage.length > 0){
                for(var i= 0;i<localStorage.length;i++){
                    this.todoItems.push(localStorage.key(i));
                }
            }
        },
        methods:{
            removeTodo(todoItem, index){
                localStorage.removeItem(todoItem);
                this.todoItems.splice(index,1); // splice(,) 배열의 특정 인텍스에서 부여한 숫자만큼의 인덱스를 삭제
            }
        }
    }
</script>

<style scoped>
    ul{list-style-type:none;text-align:left;}
    li{display:flex;min-height:50px;height:50px;line-height:50px;margin:5px 0;padding:0 10px;background:#fff;}
    .checkBtn{line-height:45px;color:#002346;margin-right:5px;}
    .removeBtn{margin-left:auto;color:#9c0000;}

</style>
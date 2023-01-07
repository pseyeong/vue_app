<template>
    <div>
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo"> <!-- v-model : 폼에 입력한 값을 뷰 인스턴스의 데이터와 즉시 동기화 -->
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3>
            <span slot="footer" @click="showModal = false">
                할 일을 입력하세요!
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>

<script>
    import Modal from './common/Modal.vue'

    export default{
        props:['propsdata'],
        data(){
            return{
                newTodoItem:'',
                showModal:false // 모달 동작을 위한 플래그 값
            }
        },
        methods:{
            addTodo(){
                if(this.newTodoItem !== ""){ // (!== 다르다) // 인풋 박스의 입력 값이 있을 때만 저장
                    var value = this.newTodoItem && this.newTodoItem.trim(); // 인풋 박스에 입력된 텍스트의 앞뒤 공백 문자열 제거
                    //localStorage.setItem(value, value);
                    this.$emit('addTodo',value);
                    this.clearInput(); // 인풋 박스 입력 값 초기화
                }else{
                    this.showModal = !this.showModal; // 텍스트 미입력 시 모달 동작
                }
            },
            clearInput(){
                this.newTodoItem = '';
            }
        },
        components:{
            Modal: Modal
        }
    }
</script>

<style scoped>
    input {border:2px solid #002346;border-radius:20px;padding:5px;font-weight:500;text-indent:10px;font-family: 'Noto Sans KR', sans-serif;width:80%}
    input::placeholder{font-size:.9rem}
    span{border:none;background:#002346;padding:5px 7px;border-radius:50%;font-size:.9rem;font-weight:600;color:#fff;margin-left:5px;}
</style>
<template>
    <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput></TodoInput>
      <TodoList></TodoList>
      <TodoFooter></TodoFooter>
    </div>
</template>

<script>
    import TodoHeader from './components/TodoHeader.vue'
    import TodoInput from './components/TodoInput.vue'
    import TodoList from './components/TodoList.vue'
    import TodoFooter from './components/TodoFooter.vue'

    export default{
      components:{
        'TodoHeader': TodoHeader,
        'TodoInput': TodoInput,
        'TodoList': TodoList,
        'TodoFooter': TodoFooter
      }
    }

    
</script>

<style>
  *{margin:0;padding:0;}
  body{text-align:center;font-family:'Ubuntu', sans-serif;background:#b9dcff}
  input{border-style:groove;width:200px;}
  button{border-style:groove;}
  .shadow{box-shadow:5px 10px 10px rgba(0,0,0,.03)}
</style>
<template>
  <div>
    <h1>Todo List</h1>

    <div v-for="todo in todos" :key="todo.id"> 
      <!-- <h3>{{ todo.title }}</h3> -->

      <!-- 
        parent component 가 아닌 grandParent component 가 event emitter 의 대상이므로 
        'methods' 사용하기 보다 이런식으로 동일한 이벤트 이름을 이용하여 간략하게 전달한다.
      -->
      <!-- 'v-bind' 생략 가능, 'v-on:' 을 '@' 대체 가능 -->
      <TodoItem 
        :todo="todo" 
        @toggle-complete="$emit('toggle-complete', todo.id)" 
        @delete-todo="$emit('delete-todo', todo.id)"
      /> 

    </div>

  </div>
</template>

<script>
  import TodoItem from './TodoItem.vue'

  export default {
    name: 'TodoList', // 반드시 multi word (2개 이상의 단어 조함)
    props: [ // 직접적인 값일 때는 'object', 바인딩 데이터일 때는 'array' 
      'todos', // 직접적인 값일 때는 'type' 표시, 바인딩 데이터일 때는 '데이터 변수명'
    ],
    components: {
      TodoItem,

    },

  }
</script>

<style scoped>

</style>

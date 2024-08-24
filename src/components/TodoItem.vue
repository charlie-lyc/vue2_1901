<template>
  <!-- 'v-bind' 생략 가능, 'v-on:' 을 '@' 로 대체 가능 -->
  <div class="todo-item" 
    :class="{'is-complete': todo.completed}"
  >

    <input type="checkbox" 
      :checked="todo.completed" 
      @change="toggleComplete"
    />

    <span> {{ todo.title }}</span>

    <!-- 
    <button class="del" 
        @click="deleteTodo"
    >X</button> 
    -->
    <button class="del"
        @click="$emit('delete-todo', todo.id)"
    >X</button>

  </div>
</template>

<script>
  export default {
    name: 'TodoItem', // 반드시 multi word (2개 이상의 단어 조함)
    props: [ // 직접적인 값일 때는 'object', 바인딩 데이터일 때는 'array' 
        'todo', // 직접적인 값일 때는 'type' 표시, 바인딩 데이터일 때는 '데이터 변수명'
    ],
    methods: {
        toggleComplete() {
        // console.log('completed item')
        // this.todo.completed = !this.todo.completed // Now, not working
        /////////////////////////////////////////////
        // console.log('toggle event emitted')
        this.$emit('toggle-complete', this.todo.id)
        },
        // deleteTodo() {
        //   this.$emit('delete-todo', this.todo.id)
        // },
    },

  }
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    text-align: left;
    }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
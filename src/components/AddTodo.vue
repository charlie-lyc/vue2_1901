<template>
  <div>
    <form @submit="addTodo">
        <input type="text" name="title" placeholder="Add Todo ..." 
            v-model="title"
        />
        <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
  export default {
    name: 'AddTodo', // 반드시 multi word (2개 이상의 단어 조함)
    methods: {
      addTodo(e) {
        e.preventDefault()
        this.$emit('add-todo', this.title)
        this.title = ''
      }
    },
    data() {
      return {
        title: '',
      }
    },

  }
</script>

<style scoped>
 form {
    display: flex;
 }
 input[type='text'] {
    flex: 10;
    padding: 5px;
 }
 input[type='submit'] {
    flex: 2;
 }
</style>
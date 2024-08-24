<template>
  <div class="hello">
    {{ msg }}
    <!-- <h1>Hello World</h1> -->
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld', // 반드시 multi word (2개 이상의 단어 조함)
    props: { // 직접적인 값일 때는 'object', 바인딩 데이터일 때는 'array' 
      msg: String, // 직접적인 값일 때는 'type' 표시, 바인딩 데이터일 때는 '데이터 변수명'
    },

  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>

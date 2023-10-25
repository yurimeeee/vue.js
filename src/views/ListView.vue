<script>
  export default{
    data() {
      return {
        parentLangs: 'Web',
        items:[
          {id:1, title:'HTML', desc:'HTML is...'},
          {id:2, title:'CSS', desc:'CSS is...'},
          {id:3, title:'Javascript', desc:'Javascript is...'}
        ],
        myObject: {
          title: 'Vue에서 목록을 작성하는 방법',
          author: '홍길동',
          publishedAt: '2016-04-10'
        },
        numbers: [1, 2, 3, 4, 5],
        sets: [[ 1, 2, 3, 4, 5 ], [6, 7, 8, 9, 10]]
      }
    },
    computed: {
    evenNumbers() {
      console.log('evenNumbers 실행')
      return this.numbers.filter(n => n % 2 === 0)  
      //computed: numbers안의 값이 변경될 때만 실행
      }
    },
    methods: { 
      even(numbers) {
        console.log('even 실행')
        return numbers.filter(number => number % 2 === 0)
        //methods: data함수 내 어느 값이 변경되던 실행(무조건 실행)
      }
    }
  }
</script>

<template>
  <div class="layout">
    <h1>This is List Rendering page</h1>
    <h2>v-for</h2>
    <ul>
      <li v-for="(item, index) in items" :key="item.id">
        {{ parentLangs }} {{ index }} {{ item.title }}
     <!-- {{ item.title }} -->
      </li>
    </ul>
   
    <hr>
    <h2>객체에 v-for 사용하기</h2>
    <ul>
      <li v-for="value in myObject" :key="value.id">
        {{ value }}
        <!-- {{ console.log(value) }}/ -->
      </li>
    </ul>

    <hr>
    <h2>숫자 범위에 v-for 사용하기</h2>
    <span v-for="n in 10" :key="n">{{ n }}</span>

    <hr>
    <h2>template에서 v-for 사용하기</h2>
    <ul>
      <template v-for="item in items" :key="item.id">
        <li>{{ item.desc }}</li>
      </template>
    </ul>

    <hr>
    <h2>필터링</h2>
    <!-- computed -->
    <ul>
      <li v-for="n in evenNumbers" :key="n">{{ n }}</li>
    </ul>
    <button @click="numbers.push(2)">+</button>
    <hr>
    <!-- methods -->
    <ul v-for="numbers in sets" :key="numbers"> 
      <!-- 반복문 안에 반복문 -->
      <li v-for="n in even(numbers)" :key="n">{{ n }}</li>
    </ul>
    <button @click="sets[0].push(2)">+</button>


 


  

  </div>
</template>




<style>

</style>
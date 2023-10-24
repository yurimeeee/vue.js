<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  },
  msg2:{
    type: String,
    required: true
  }
})
const rawHTML = '<a href="">Link</a>';
const pid = 10;
const isButtonDisabled = true;
const objectOfAttrs = {
      id: 'container',
      class: 'wrapper'
    }
const number = 20;
const ok = false;
const message = '안녕하세요';
const id = 30;

const sayHello = (msg)=>{
  alert(msg);
}
const url = "http://google.com";
const attributeName = 'href';

const items = [
  {id:0, title:'html'},
  {id:1, title:'css'},
  {id:2, title:'javascript'},
]

const onSubmit = ()=>{
  alert('제출완료');
}
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }} {{ msg2 }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <hr>
    <h2>HTML 출력</h2>
    <p>{{ rawHTML }}</p> <!-- html 출력 -->
    <p><span  v-html="rawHTML"></span></p>  <!-- 텍스트 출력-->

    <hr>
    <h2>속성 바인딩</h2>
    <div v-bind:id ="pid"></div>
    <div :id ="pid"></div>
    <div id ="pid"></div>  
    <div id ="{{pid}}"></div> 
   
    <hr>
    <h2>불리언 바인딩</h2>
    <button disabled="true">버튼</button> <!--변경 불가-->
    <button :disabled="isButtonDisabled">버튼</button> <!--비활성-->
    <button :disabled="!isButtonDisabled">버튼</button> <!--활성-->
   
    <hr>
    <h2>여러 속성 바인딩</h2>
    <div v-bind="objectOfAttrs"></div>

    <hr>
    <h2>JavaScript 표현식</h2>
    {{ number + 1 }}
    {{ ok ? '예' : '아니오' }}
    {{ message.split('').reverse().join('') }}
    <div :id="`list-${id}`"></div>

    <hr>
    <h2>함수 호출</h2>
    <!-- <span :title="sayHello('안녕하세요')"></span>
    <div>{{ sayHello('안녕하세요') }}</div> -->

    <hr>
    <h2>디렉티브 - 인자</h2>
    <a v-bind:href="url"> Link </a>
    <!-- 단축 문법 -->
    <a :href="url"> Link </a>
    <a v-bind:[attributeName]="url"> Link </a>

    <h2>v-on</h2>
    <div>
      <button type="button" v-on:click="sayHello('클릭이벤트')">click</button>
      <button type="button" @click="sayHello('클릭이벤트')">click</button>
      <button type="button" @mouseover="sayHello('클릭이벤트')">click</button>
    </div>
    <form action="" @submit.prevent="onSubmit">
      <button>제출</button>
    </form>


    <hr>
    <h2>v-for</h2>
    <!-- for in 은 객체여야 함 -->
    <div v-for="item in items" :key="item.id">
      {{ item.title }}
    </div>


  </div>
  
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>

<script>
  export default{
    data() {
      return {
       count:0,
       name:'Vue.js'
      }
    },
    methods: {
    greet(event) {
      // `this`는 메서드가 활성화된 현재 인스턴스
      alert(`안녕 ${this.name}!`)
      // 'event'는 네이티브 DOM 이벤트 객체입니다.
      if (event) {
        alert(event.target.tagName)
      }
    },
    say(message) {
      alert(message)
    },
    warn(message, event) {
    // 이제 네이티브 이벤트 객체에 접근할 수 있습니다.
    if (event) {
      event.preventDefault()
    }
    alert(message)
    }, 
    doThis(){
      //.stop
      alert('링크 전파를 차단했습니다.')
    },
    onSubmit(){
      //.onSubmit
      alert('폼 제출을 막았습니다.')
    },
    doThat(){
      //.stop.prevent
      alert('기본 속성 차단, 링크 전파를 차단했습니다.')
    },
    boxClick(){
      alert('boxClick.')
    },
    spanClick(){
      alert('spanClick.')
    },
    submit(){
      alert('enter키가 입력되었습니다.')
    },
    onPageDown(){
      alert('onPageDown키가 입력되었습니다.') 
    }
  }
}
</script>


<template>
  <div class="layout">
    <h1>This is Event Handler page</h1>

    <h2>인라인 핸들러</h2>
    <button @click="count++">1추가</button>
    <p>숫자 값: {{ count }}</p>


    <hr>
    <h2>메서드 핸들러</h2>
    <button @click="greet">환영하기</button>

    <hr>
    <h2>인라인 핸들러에서 메서드 호출하기</h2>
    <button @click="say('안녕')">안녕이라고 말하기</button>
    <button @click="say('잘가')">잘가라고 말하기</button>

    <hr>
    <h2>인라인 핸들러에서 이벤트 객체 접근하기</h2>
        <!-- 특수한 키워드인 $event 사용 -->
    <button @click="warn('아직 양식을 제출할 수 없습니다.', $event)">
      제출하기
    </button>

    <!-- 인라인 화살표 함수 사용 -->
    <button @click="(event) => warn('아직 양식을 제출할 수 없습니다.', event)">
      제출하기
    </button>

    <hr>
    <h2>이벤트 수식어</h2>
    <!-- click 이벤트가 부모에게 전파x (버블링x) -->
    <a @click.stop="doThis" href="https://www.naver.com/" target="_blank">doThis</a>

    <!-- submit 이벤트가 더 이상 페이지 리로드 x -->
    <form @submit.prevent="onSubmit" action="https://www.naver.com/">
      <button>제출</button>
    </form>

    <!-- 수식어 연결 가능 -->
    <a @click.stop.prevent="doThat"  href="https://www.naver.com/" target="_blank">doThat</a>

    <!-- 이벤트 핸들러 없이 수식어만 사용 가능 -->
    <form @submit.prevent action="https://www.naver.com/">
      <button>제출</button>
    </form>


    <!-- event.target이 엘리먼트 자신일 경우에만 핸들러가 실행됩니다. -->
    <!-- 예를 들어 자식 엘리먼트에서 클릭 액션이 있으면 핸들러가 실행되지 않습니다. -->
    <div @click="boxClick" class="box">
      <span @click="spanClick" class="box">click</span>
    </div>
    <div @click.self="boxClick" class="box">
      <span @click.self="spanClick" class="box">click</span>
    </div>

    <hr>
    <h2>입력키 수식어</h2>
    <!-- `key`가 `Enter`일 때만 `submit`을 호출합니다 -->
    <input @keyup.enter="submit" />
    <input @keyup.page-down="onPageDown" />



  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
  .box{
    border: 1px solid;
    padding: 20px;
    display: inline-block;

  }
}
</style>

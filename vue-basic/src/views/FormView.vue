<script>
export default{
  data(){
    return{
      message:'',
      multipleMsg:'',
      checked:true,
      checkedNames: [],
      picked :'하나',
      // selected :''
      selected: '1',
      options: [
        { text: '하나', value: '1' },
        { text: '둘', value: '2' },
        { text: '셋', value: '3' }
      ],
      toggle:false,
      dynamicTrueValue:'네',
      dynamicFalseValue:'아니오',
      pick:'',
      first:'네',
      second:'아니오'
    }
  }
}

</script>

<template>
  <div class="layer">
    <h1>This is Form Input Bindings page</h1>

    <h2>텍스트</h2>
    <!-- <input type="text" :value="message" @input="event=>message=event.target.value"> -->
    <!-- 위 코드 단축 -->
    <input v-model="message">
    <p>메세지 :{{ message }}</p>

    <hr>
    <h2>여러 줄 텍스트</h2>
    <span>여러 줄 메세지:</span>
    <p style="white-space: pre-line;">{{ multipleMsg }}</p>
    <textarea v-model="multipleMsg" placeholder="여러 줄을 추가해보세요"></textarea>

    <hr>
    <h2>체크박스</h2>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>

    <!-- 기존 값을 지우고 자동으로 true 만 출력 -->
    <div>체크된 이름: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="젝" v-model="checkedNames">
    <label for="jack">젝</label>

    <input type="checkbox" id="john" value="존" v-model="checkedNames">
    <label for="john">존</label>

    <input type="checkbox" id="mike" value="마이크" v-model="checkedNames">
    <label for="mike">마이크</label>

    <hr>
    <h2>라디오</h2>
    <div>선택한 것: {{ picked }}</div>

    <input type="radio" id="one" value="하나" v-model="picked" />
    <label for="one">하나</label>

    <input type="radio" id="two" value="둘" v-model="picked" />
    <label for="two">둘</label>

    <hr>
    <h2>셀렉트</h2>
    <div>선택됨: {{ selected }}</div>

    <select v-model="selected">
      
    <!-- vue에서 자동으로 value 넣어줌(대신, 텍스트와 value가 일치할 때) -->
      <option disabled value="">다음 중 하나를 선택하세요</option>
      <option>가</option>
      <option>나</option>
      <option>다</option>
    </select>

    <h2>다중선택 셀렉트</h2>
    <div>선택됨: {{ selected }}</div>

    <select v-model="selected" multiple>
      <option>가</option>
      <option>나</option>
      <option>다</option>
    </select>


    <select v-model="selected">
      <option v-for="option in options" :value="option.value" :key="option">
        {{ option.text }}
      </option>
    </select>

    <div>선택됨: {{ selected }}</div>

    <hr>
    <h2>값 바인딩 하기</h2>
    <!-- `picked`는 선택 시 문자열 "가"입니다. -->
    <input type="radio" v-model="picked" value="가" />

    <!-- `toggle`은 true 또는 false입니다. -->
    <input type="checkbox" v-model="toggle" />

    <!-- `selected`는 첫 번째 옵션이 선택될 때 문자열 "한글"입니다. -->
    <select v-model="selected">
      <option value="한글">한글</option>
    </select>


    <P>Checkbox</P>
    <input
    type="checkbox"
    v-model="toggle"
    :true-value="dynamicTrueValue"
    :false-value="dynamicFalseValue" />
    {{ toggle }}

    <P>radio</P>
    <input type="radio" v-model="pick" :value="first" />
    <input type="radio" v-model="pick" :value="second" />
    {{ pick }}


    <hr>
    <h2>수식어</h2>
    <p>lazy</p>
    <!-- "input" 대신 "change" 이벤트 후에 동기화됨 -->
    <input v-model="msg" /> <!-- "input" 입력하는 순간 실행 -->
    <input v-model.lazy="msg" /><!-- "input" 다 입력하고 나서 실행 -->
    {{ msg }}

  </div>
</template>


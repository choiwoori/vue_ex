<script>
export default{
  data() {
    return {
      count: 0,
      name: 'Vue.js'
    }
  },
  methods: {
    greet(event) {
      // `this`는 메서드가 활성화된 현재 인스턴스를 가리킵니다.
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
    }
  }
}


</script>


<template>
  <div class="layout">
    <h1>This is an Event Handling page</h1>

    <h2>인라인 핸들러</h2>
    <button @click="count++">1 추가</button>
    <p>숫자 값은: {{ count }}</p>

    <h2>메서드 핸들러</h2>
    <!-- `greet`는 위에서 정의한 메서드의 이름입니다. -->
    <button @click="greet">환영하기</button>

    <h2>인라인 핸들러에서 메서드 호출하기</h2>
    <button @click="say('안녕')">안녕이라고 말하기</button>
    <button @click="say('잘가')">잘가라고 말하기</button>

    <h2>인라인 핸들러에서 이벤트 객체 접근하기</h2>
    <!-- 특수한 키워드인 $event 사용 -->
    <button @click="warn('아직 양식을 제출할 수 없습니다.', $event)">제출하기</button>

    <!-- 인라인 화살표 함수 사용 -->
    <button @click="(event) => warn('아직 양식을 제출할 수 없습니다.', event)">제출하기</button>




  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

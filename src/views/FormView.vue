<script>
export default{
  data() {
    return {
      message:'',
      multiple:'',
      checked:true,
      checkedNames: []
    }
  }
}


</script>


<template>
  <div class="layout">
    <h1>This is an Form Input Bindings page</h1>
    <h2>텍스트</h2>
    <!--input type="text" :value="message" @input="event=>message=event.target.value"-->
    <input v-model="message">
    <!--v-model 단점: 영어만 실시간으로 반영-->
    <p>메세지{{ message }}</p>

    <h2>여러 줄 텍스트</h2>
    <span>여러 줄 메세지:</span>
    <p style="white-space: pre-line;">{{ multiple }}</p>
    <textarea v-model="multiple" placeholder="여러 줄을 추가해보세요"></textarea>

    <h2>체크박스</h2>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>

    <div>체크된 이름: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="젝" v-model="checkedNames">
    <label for="jack">젝</label>

    <input type="checkbox" id="john" value="존" v-model="checkedNames">
    <label for="john">존</label>

    <input type="checkbox" id="mike" value="마이크" v-model="checkedNames">
    <label for="mike">마이크</label>

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

<template>
  <header>
    <h1>TODO it!</h1>
  </header>
</template>

<script>
export default {
  name: "TodoHeader"
}
</script>

<!--scoped: 해당 컴포넌트 안에서만 유효한 스타일 속성 부모자식간의 영향을 받지 않음-->
<style scoped>
h1 {
  color: #2F3B52;
  font-weight: 900;
  /*rem: */
  margin: 2.5rem 0 1.5rem;
}
</style>
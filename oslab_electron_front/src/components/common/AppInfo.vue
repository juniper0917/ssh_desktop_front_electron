<template>
  <img class="sshdesktopicon" src="@/assets/right-arrow-angle-and-horizontal-down-line-code-signs.png">
  <div class="text1">SSH Desktop</div>
  <div class="text2">Build 2312</div>
  <div class="line">
    <img class="size" src="@/assets/twitter.png">
    <img class="size" src="@/assets/github.png">
  </div>

</template>

<script>
  export default {
  name: 'AppInfo',
  }
</script>

<style scoped>
.sshdesktopicon{
  width: 4rem;
  height: 4rem;
  background-color: #D9D9D9;
  border-radius: 0.5rem;
  display: block;
  margin-top: 9rem;
  margin-left: auto;
  margin-right: auto;
}
.text1{
  text-align: center;
  color: white;
  font-weight: 500;
  display: block;
  margin-top: 1rem;
  margin-left: auto;
  margin-right: auto;
}
.text2{
  text-align: center;
  color: #AAAAAA;
  font-weight: 500;
  display: block;
  margin-top: 1rem;
  margin-left: auto;
  margin-right: auto;
}
.line{
  display: block;
  margin-top: 1rem;
  margin-left: auto;
  margin-right: auto;
  display: flex; 
  justify-content: center;
}
.size{
  margin-left: 0.2rem;
  margin-right: 0.2rem;
  width: 1rem;
  cursor:pointer;
}
</style>
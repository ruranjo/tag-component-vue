<script setup>
  import InputTag from "./components/InputTag.vue"
</script>

<template>
  <div class="App">
    <div class="logo">TAG-COMPONENT</div>
    <InputTag/>
  </div>
</template>

<style scoped>

  .logo{
    font-size: 64px ;
    font-weight: 800;
    margin: 3rem;
    color: #34495E;
  }

  @media (max-width:  460px){
    .logo{
      font-size: 32px ;
    }
  }

</style>

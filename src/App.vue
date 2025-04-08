<template>
  <myHeader />
  <MyLateralMenu/>
  <MyAtividade/>
  
</template>

<script>
  import MyAtividade from './components/myAtividade.vue';
  import myHeader from './components/myHeader'
  import MyLateralMenu from './components/myLateralMenu.vue';
  
  export default {
    name: 'App',
    components: {
      myHeader, MyLateralMenu, MyAtividade
    }
  }
</script>

<style>

</style>

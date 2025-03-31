<template>
  <myHeader />
  <MyLateralMenu/>
  <!-- <myComments /> -->
</template>

<script>
  // import myComments from './components/myComments'
  import myHeader from './components/myHeader'
  import MyLateralMenu from './components/myLateralMenu.vue';
  
  export default {
    name: 'App',
    components: {
      myHeader, MyLateralMenu
    }
  }
</script>

<style>

</style>

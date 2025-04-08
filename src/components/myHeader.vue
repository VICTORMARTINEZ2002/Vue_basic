<script setup>
import logoSesi from '@/assets/logoSESI.png';
import logoErgotech from '@/assets/logoErgotech.png';
</script>

<template>
  <header class="header">
    <div class="logo-container">
      <img :src="logoSesi"     alt=    "Logo Sesi" class=    "logoSESI" />
      <img :src="logoErgotech" alt="Logo Ergotech" class="logoErgotech" />
    </div>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  display: flex;
  padding: 1rem 2rem;
  background-color: #14637F;
  height: 60px;
  width: 100%;
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.logoSESI {
  height: 40px;
}

.logoErgotech {
  height: 50px;
}

</style>

<script setup>
import logoSesi from '@/assets/logoSESI.png';
import logoErgotech from '@/assets/logoErgotech.png';
</script>

<template>
  <header class="header">
    <div class="logo-container">
      <img :src="logoSesi" alt="Logo Sesi" class="logoSESI" />
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
  align-items: center;
  padding: 1rem 2rem;
  background-color: #14637F;
  height: 60px;
  width: 100%;
  box-sizing: border-box;
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.logoSESI {
  height: 40px;
}

.logoErgotech {
  height: 50px;
}

.title {
  margin: 0;
  font-size: 1.5rem;
}

.nav-list {
  list-style: none;
  display: flex;
  gap: 1rem;
  margin: 0;
  padding: 0;
}

.nav-list a {
  color: white;
  text-decoration: none;
}

.nav-list a:hover {
  text-decoration: underline;
}
</style>

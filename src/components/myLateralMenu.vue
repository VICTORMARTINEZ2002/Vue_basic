<template>
    <div class="container">
      <ul class="menu-list">
        <li class="menu-item">
          <img :src="InicioIcon" alt="INÍCIO" class="menu-icon">
          <a href="#" class="menu-link-main">INÍCIO</a>
        </li>
        <li class="menu-item">
          <img :src="GerenciarIcon" alt="GERENCIAR" class="menu-icon">
          <a href="#" class="menu-link-main">GESTÃO DE USUÁRIOS</a>
        </li>
        <li class="menu-item">
          <img :src="ClientesIcon" alt="CLIENTES" class="menu-icon">
          <a href="#" class="menu-link-main">EMPRESAS CLIENTES</a>
        </li>
        <li class="menu-item with-submenu">
          <div class="menu-content">
            <img :src="DemandasIcon" alt="DEMANDAS" class="menu-icon">
            <a href="#" class="menu-link-main">DEMANDAS</a>
          </div>
          <ul class="submenu">
            <li class="submenu-item">
              <img :src="TarefasIcon" alt="TAREFAS" class="menu-icon">
              <a href="#" class="menu-link-main">TAREFAS</a>
            </li>
            <li class="submenu-item">
              <img :src="AtividadesIcon" alt="ATIVIDADES" class="menu-icon">
              <a href="#" class="menu-link-main">ATIVIDADES</a>
            </li>
            <li class="submenu-item">
              <img :src="AvaliacoesIcon" alt="AVALIAÇÕES" class="menu-icon">
              <a href="#" class="menu-link-main">AVALIAÇÕES</a>
            </li>
          </ul>
        </li>
        <li class="menu-item">
          <img :src="DuvidasIcon" alt="DÚVIDAS" class="menu-icon">
          <a href="#" class="menu-link-main">DÚVIDAS FREQUENTES</a>
        </li>
        <li class="menu-item">
          <img :src="SairIcon" alt="SAIR" class="menu-icon">
          <a href="#" class="menu-link-main">SAIR</a>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import AtividadesIcon from '@/assets/MenuLateral/Atividades.png';
  import AvaliacoesIcon from '@/assets/MenuLateral/Avaliações.png';
  import ClientesIcon from '@/assets/MenuLateral/Clientes.png';
  import DemandasIcon from '@/assets/MenuLateral/Demandas.png';
  import DuvidasIcon from '@/assets/MenuLateral/Duvidas.png';
  import GerenciarIcon from '@/assets/MenuLateral/Gerenciar.png';
  import InicioIcon from '@/assets/MenuLateral/Inicio.png';
  import SairIcon from '@/assets/MenuLateral/Sair.png';
  import TarefasIcon from '@/assets/MenuLateral/Tarefas.png';
  import TrabalhadoresIcon from '@/assets/MenuLateral/Trabalhadores.png';
  
  export default {
    data() {
      return {
        AtividadesIcon,
        AvaliacoesIcon,
        ClientesIcon,
        DemandasIcon,
        DuvidasIcon,
        GerenciarIcon,
        InicioIcon,
        SairIcon,
        TarefasIcon,
        TrabalhadoresIcon
      };
    }
  };
  </script>
  
  <style scoped>
  .container {
    color: #000;
    position: fixed;
    top: 60px; /* abaixo do header fixo */
    left: 0;
    width: 25vw;
    height: calc(100vh - 60px); /* para não ultrapassar a tela abaixo do header */
    background-color: #ffffff;
    padding-left: 1rem;
    box-sizing: border-box;
    overflow-y: auto;
  }
  
  .menu-list {
    list-style-type: none;
    padding-left: 0;
  }
  
  .menu-item {
    display: flex;
    align-items: center;
    margin-top: .75rem;
    margin-bottom: 0.5rem;
    height: 100%;
    padding: 0.2rem 0;
  }
  
  .menu-item.with-submenu {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
  
  .menu-content {
    display: flex;
    align-items: center;
    width: 100%;
  }
  
  .submenu {
    list-style-type: none;
    width: 100%;
    padding-left: 2.5rem;
    margin-top: 0.5rem;
  }
  
  .submenu-item {
    display: flex;
    align-items: center;
    margin-top: 0.5rem;
    height: 100%;
    padding: 0.3rem 0;
  }
  
  .menu-icon {
    width: 34px;
    height: 34px;
    margin-right: 1rem;
  }
  
  .menu-link-main {
    font-size: 1.125rem;
    font-weight: 600;
    text-decoration: none;
    color: inherit;
  }
  
  
  .menu-link-main:hover,
  .menu-link-main:hover {
    color: #14637F;
  }
  </style>
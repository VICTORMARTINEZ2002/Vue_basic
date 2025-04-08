<template>
    <div class="atividade-container">
      <div class="form-wrapper">
        <h1 class="page-title">Cadastrar Atividade</h1>
  
        <div class="form-content">
          <myComboBox
            label="SELECIONE A EMPRESA:"
            :items="empresas"
            v-model="empresaSelecionada"
          />
  
          <myComboBox
            label="SELECIONE A DEMANDA:"
            :items="demandas"
            v-model="demandaSelecionada"
          />
  
          <myComboBox
            label="SELECIONE A TAREFA:"
            :items="tarefas"
            v-model="tarefaSelecionada"
          />
  
          <myInputText
            id="atividade"
            label="NOME DA ATIVIDADE:"
            placeholder="Digite aqui..."
            v-model="atividade"
          />
  
          <MyTextArea
            id="descrição"
            label="DESCRIÇÃO DA ATIVIDADE:"
            placeholder="Digite aqui..."
            v-model="descrição"
            :height="120"
          />
  
          <div class="slider-wrapper">
            <MyImageSlider :imagePaths="imagePaths" />
          </div>

          <MyButton label="Salvar" @click="salvarAtividade" />
        <MyButton label="Cancelar" :disabled="true" />

        </div>
      </div>
    </div>
  </template>
  
  <script>
  import myComboBox    from './ComboBox/myComboBox.vue';
  import myInputText   from './InputText/myInputText.vue';
  import MyTextArea    from './InputText/myTextArea.vue';
  import MyImageSlider from './ImageSlider/myImageSlider.vue';
  import MyButton from './Botão/MyButton.vue';
  
  export default {
    name: 'MyAtividade',
    components: {
      myComboBox,
      myInputText,
      MyTextArea,
      MyImageSlider,
      MyButton
    },
    data() {
      return {
        empresas: [
        { id: 1, nome: 'Tech Solutions Ltda' },
        { id: 2, nome: 'Construtora Alpha' },
        { id: 3, nome: 'Logística Beta' },
        ],
        demandas: [
          { id: 1, nome: 'Implementar Sistema ERP' },
          { id: 2, nome: 'Reformar Escritório Central' },
          { id: 3, nome: 'Otimizar Rota de Entregas' },
        ],
        tarefas: [
          { id: 1, nome: 'Levantamento de Requisitos' },
          { id: 2, nome: 'Execução da Obra' },
          { id: 3, nome: 'Teste de Eficiência' },
        ],
        empresaSelecionada: '',
        demandaSelecionada: '',
        tarefaSelecionada: '',
        atividade: '',
        descrição: '',
        imagePaths: [],
      };
    },
    mounted() {
      this.buscarEmpresas();
      this.buscarDemandas();
      this.buscarTarefas();
      this.buscarImagens();
    },
    methods: {
      async buscarEmpresas() {
        try {
          const resposta = await fetch('/api/empresas');
          this.empresas = await resposta.json();
        } catch (erro) {
          console.error('Erro ao buscar empresas:', erro);
        }
      },
      async buscarDemandas() {
        try {
          const resposta = await fetch('/api/demandas');
          this.demandas = await resposta.json();
        } catch (erro) {
          console.error('Erro ao buscar demandas:', erro);
        }
      },
      async buscarTarefas() {
        try {
          const resposta = await fetch('/api/tarefas');
          this.tarefas = await resposta.json();
        } catch (erro) {
          console.error('Erro ao buscar tarefas:', erro);
        }
      },
      async buscarImagens() {
        this.imagePaths = [];

        for(let i=1; i<=950; i++){
          this.imagePaths.push(`/imagens/ImageCapture${i}.jpg`);
        }

        

        // try {
        //   const resposta = await fetch('/api/imagens');
        //   const imagens = await resposta.json();
  
        //   // Se o backend retornar apenas nomes de arquivos
        //   this.imagePaths = imagens.map(nome => `/uploads/${nome}`);
  
        //   // Se o backend já retornar URLs completas, basta usar:
        //   // this.imagePaths = imagens;
  
        // } catch (erro) {
        //   console.error('Erro ao buscar imagens:', erro);
        // }
      },
    },
  };
  </script>
  
  <style scoped>
  .atividade-container {
    position: absolute;
    margin-top: 50px;
    left: 25vw;
    width: 75vw;
    top: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #ffffff;
    box-sizing: border-box;
  }
  
  .form-wrapper {
    width: 100%;
    max-width: 800px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    }

  
  .page-title {
    font-size: 2.5rem;
    font-weight: bold;
    color: #000000;
    text-align: center;
    margin-bottom: 20px;
  }
  
  .form-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0px;
  }
  
  .form-content > * {
    width: 100%;
    max-width: 600px;
  }
  
  .slider-wrapper {
    width: 100%;
    text-align: center;
    margin-top: 30px;
  }
  
  .slider-title {
    font-size: 1.5rem;
    margin-bottom: 10px;
  }
  </style>
  
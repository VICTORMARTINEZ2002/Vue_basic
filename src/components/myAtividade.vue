<template>
  <div class="container">
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

        <div class="half-combos">
          <MyHalfComboBox
            label="INÍCIO DA ATIVIDADE:"
            :items="imageIndex"
            v-model="inicioSelecionado"
          />
          <MyHalfComboBox
            label="FIM DA ATIVIDADE:"
            :items="imageIndex"
            v-model="fimSelecionado"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import myComboBox from './ComboBox/myComboBox.vue';
import myInputText from './InputText/myInputText.vue';
import MyTextArea from './InputText/myTextArea.vue';
import MyImageSlider from './ImageSlider/myImageSlider.vue';
import MyHalfComboBox from './ComboBox/myHalfComboBox.vue';

export default {
  name: 'MyAtividade',
  components: {
    myComboBox,
    myInputText,
    MyTextArea,
    MyImageSlider,
    MyHalfComboBox,
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
      imageIndex: [],
      inicioSelecionado: '',
      fimSelecionado: '',
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
      for (let i = 1; i <= 950; i++) {
        this.imagePaths.push(`/imagens/ImageCapture${i}.jpg`);
      }

      this.imageIndex = this.imagePaths.map((path, index) => ({
        id: index + 1,
        nome: path.split('/').pop(), // Exibe só o nome do arquivo
      }));
    },
  },
};
</script>

<style scoped>
.container {
  min-height: 100vh;
  width: 75vw;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffffff;
  box-sizing: border-box;
  margin-top: 60px;
}

.form-wrapper {
  width: 100%;
  max-width: 800px;
  padding: 20px;
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 12px;
}

.page-title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #000000;
  text-align: center;
  margin-bottom: 20px;
}

.form-content {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.form-content > * {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
}

.slider-wrapper {
  width: 100%;
  max-width: 600px;
  text-align: center;
  margin-top: 30px;
}

.half-combos {
  display: flex;
  gap: 1rem;
  width: 100%;
  max-width: 600px;
}
</style>

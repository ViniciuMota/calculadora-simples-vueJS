<script setup>
    import { reactive } from 'vue';
    const estado = reactive({
        primeiroValor:0,
        segundoValor:0,
        operacao:'soma',
        resultado:0,
    })

   
const trocarFiltro = (event) => {
  estado.operacao = event.target.value;
  calcular();
}

const gravaprimeiroValor = (event) => {
  estado.primeiroValor = event.target.value;
  calcular();
}

const gravasegundoValor = (event) => {
  estado.segundoValor = event.target.value;
  calcular();
}

const calcular = () => {
  let resultado = 0;
  let { operacao, primeiroValor, segundoValor } = estado;
  
  switch (operacao) {
    case 'adicao':
      resultado = parseInt(primeiroValor) + parseInt(segundoValor);
      break;
    case 'subtracao':
      resultado = parseInt(primeiroValor) - parseInt(segundoValor);
      break;
    case 'multiplicacao':
      resultado = parseInt(primeiroValor) * parseInt(segundoValor);
      break;
    case 'divisao':
      resultado = parseInt(primeiroValor) / parseInt(segundoValor);
      break;
    default:
      resultado = 0;
      break;
  }
  estado.resultado = resultado;
}
</script>

<template>
    <div class="container">
        <header class="p-5 mb-4 mt-4 bg-light rounded-3">
            <h1>Calculadora</h1>
        </header>
        <div class="row">
            <div class="col-md-4">
                <input  @keyup="gravaprimeiroValor" type="number" placeholder="Digite aqui um valor" class="form-control" />
            </div>
            <div class="col-md-4">
                <select @change="trocarFiltro" class="form-control">
                    <option value="nada">Escolha uma operação</option>
                    <option value="adicao">Mais (+)</option>
                    <option value="subtracao">Menos (-)</option>
                    <option value="multiplicacao">Multiplicador por (x)</option>
                    <option value="divisao">Dividido por (/)</option>
                </select>
            </div>
            <div class="col-md-4">
                <input  @keyup="gravasegundoValor" type="number" placeholder="Digite aqui mais um valor" class="form-control" />
            </div>
        </div>
        <div class="col-md-12">
          <h1>{{ estado.resultado }}</h1>
        </div>
    </div>
</template>

<style scoped>
    
</style>
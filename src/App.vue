<script setup>
import { reactive } from 'vue';

const estado = reactive({
  selected: '',
  NumerosA: 0,
  NumerosB: 0,
  Result: 0,
})

function NumberSwitch(event){
  estado.NumerosA = event.target.value
}

function InputB(e){
  estado.NumerosB = e.target.value
}

function Resultado(){
  const { NumerosA, NumerosB, selected } = estado
  if (selected === "+") {
    return Number(NumerosA) + Number(NumerosB);
  } else if (selected === "-") {
    return Number(NumerosA) - Number(NumerosB);
  } else if (selected === "/") {
    return Number(NumerosA) / Number(NumerosB);
  }else if(selected === "*"){
    return Number(NumerosA) * Number(NumerosB)
  }
  else {
    return 0; 
  }
  
}
</script>

<template>
    <div class="calc">
      <h1>
      Calculadora
      </h1>

    <input type="number" name="NumberA" id="NumA" @keyup="NumberSwitch" placeholder="Digite um valor"><br>

    <select v-model="estado.selected">
      <option disabled value="">Selecione um operção</option>
      <option value="+">Adição + </option>
      <option value="-">Subtração - </option>
      <option value="/">Divisão / </option>
      <option value="*">Multiplicação x </option>
    </select><br>

    <input type="number" name="NumberB" id="NumB" @keyup="InputB" placeholder="Digite um valor">

    <div>Numero: {{ estado.NumerosA }}</div>
    <div>Numero: {{ estado.NumerosB }}</div>
    <div>Resultado: {{ Resultado() }}</div>
    </div>
</template>

<style scoped>  
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700;900&display=swap');
  .calc{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  *{
    font-family: 'Roboto', sans-serif;
  }
  input{
    margin-bottom: 18px;
    margin-top: 12px;
    font-size: 18px;
    width: 220px;
    border: none;
    border-bottom: 1px solid #000;
    outline: none;
  }
  select{
    border: none;
    border-bottom: 2px solid #000;
    font-size: 18px;
    outline: none;
  }
</style>

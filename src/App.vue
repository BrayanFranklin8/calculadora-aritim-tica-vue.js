<script setup>
import { reactive } from 'vue';

    const numero = reactive({
      numero1: 0,
      numero2: 0,
      operador: "+",
      resultado: 0,
    })

    function calcula(){
    const n1= parseFloat(numero.numero1) 
    const n2= parseFloat(numero.numero2) 
    
    switch (numero.operador){
      case '+':
        numero.resultado = n1+n2;
        break;

      case '-':
        numero.resultado = n1-n2;
        break;

      case '*':
        numero.resultado = n1*n2;
        break;
        
      case '/':
        numero.resultado = n2 !== 0? n1/n2 : "erro de divisão por zero";
        break;

        default:
          numero.resultado = 'operador invalido'

    }
    }


</script>

<template>

<div class="container">
    <div class="row">
    <div class="col">
      <header>
        <h1 class="mt-2">Calculadora aritimética</h1>
      </header>
    </div>
    <form>
      <input @keyup="evento => {numero.numero1 = evento.target.value; calcula()}"  class="m-1"  type="number" placeholder="insira o numero">
      <select @change="evento => {numero.operador = evento.target.value;calcula();}" class="m-1 p-1" >
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
      </select>
      <input @keyup="evento => {numero.numero2 = evento.target.value;calcula()}" class="m-1" type="number" placeholder="insira o numero">
      = {{ numero.resultado }}
    </form>
  </div>
</div>

</template>

<style scoped>


.container{
  margin: 200px auto;
  max-width: 900px;
  border-radius: 30px;
  background-color: #bc92d5;
  border: 1px solid black;
}

input{
  height: 34px;

}

header{
  display: flex;
  padding: 50px;
  
}

form{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 50px;
  background-color: rgb(174, 228, 223);

}

h1{
  margin: 0 auto;
}
</style>

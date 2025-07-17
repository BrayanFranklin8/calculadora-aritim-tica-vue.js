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
          <option value="+"><i class="bi bi-plus-circle">+</i></option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
      </select>
      <input @keyup="evento => {numero.numero2 = evento.target.value;calcula()}" class="m-1" type="number" placeholder="insira o numero">
      <img src="./images/equal1.png" alt="simbolo do igual">
      <div class="resultado">
        {{ numero.resultado }}
      </div>
    </form>
  </div>
</div>


</template>

<style scoped>


.container{
  margin: 200px auto;
  max-width: 900px;
  border-radius: 30px;
  background-color: #51425f;
  border: 3px solid  #2e1437;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 1);
}

input{
  height: 34px;
  background-color: #cad1c3;
  border: 2px solid #51425f;
}
input:focus{
  outline: none;
}

select{
  font-size: 20px;
  height: 34px;
  background-color: #cad1c3;
  border: 2px solid #51425f;
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
  background-color: #412a49;
  border-bottom-right-radius:30px ;
  border-bottom-left-radius:30px ;
}

img{
  width: 30px;
  height: 30px;
  margin: 0 12px;
}

h1{
  margin: 0 auto;
  color: #e7eed0;
}

.resultado{
  min-width: 32px;
  min-height: 34px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid #e7eed0;
  background-color:#cad1c3;
}

@media (max-width:764px){
  form{
    display: grid;
  }

  img{
    margin: 16px auto;
  }

  .container{
    margin-top: 32px;
  }

  h1{
  margin:0 50px ;
  color: #e7eed0;
}


}

</style>

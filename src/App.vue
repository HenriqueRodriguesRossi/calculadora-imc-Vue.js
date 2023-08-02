<template>
  <div>
    <h1>Calculadora de IMC</h1>

    <div class="form">
      <label>Peso: </label>
      <input type="number" placeholder="peso" v-model="peso"> 

      <label>Altura: </label>
      <input type="number" placeholder="altura" v-model="altura">

      <button class="calculaButton" @click="calcular()">Calcular</button>
      <span>{{ resultado }}</span>
    </div>
  </div>
</template>

<script>
export default{
  data(){
    return{
      peso: 0,
      altura: 0,
      resultado: ""
    }
  },
  methods:{
    calcular(){
      if (this.peso == 0 || this.altura == 0){
        alert("Preencha todos os campos!")


        /*Esse return vazio seria a mesma coisa que o break do switch, ou seja, se entrar nesse if irá parar a execução nesse return*/
        return
      }

      let imc = (this.peso / (this.altura ** 2)).toFixed(2)

      if(imc < 18.5){
        this.resultado = `O seu IMC é: ${imc} - Abaixo do peso!`
      }else if (imc > 18.5 && imc <= 25){
        this.resultado = `O seu IMC é: ${imc} - Peso ideal!`
      }else if(imc > 25 && imc <= 30){
        this.resultado = `O seu IMC é: ${imc} - Sobrepeso!`
      }else if(imc > 30 && imc <= 35){
        this.resultado = `O seu IMC é: ${imc} - Obesidade grau 1!`
      }else if(imc > 35 && imc <= 40){
        this.resultado = `O seu IMC é: ${imc} - Obesidade grau 2!`
      }else if(imc > 40){ 
        this.resultado = `O seu IMC é: ${imc} - Obesidade grau 3!`
      }else{
        this.resultado = "Não foi possível calcular o seu IMC!"
      }
    }  
  },
}
</script>

<style scoped>
  .form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .form input{
    background-color: whitesmoke;
    width: 300px;
    height: 35px;
    outline: none;
    border: 2px solid grey;
    color: black;
    border-radius: 30px;
  }

  .form .calculaButton{
    width: 300px;
    height: 35px;
    border: 2px solid grey;
    background-color: white;
    color: black;
    border-radius: 30px;
    cursor: pointer;
    font-weight: 600;
  }
</style>

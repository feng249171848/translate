<template>
  <div class="" id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-bind:translatedText="translatedText"></translateOutput>
  </div>
</template>

<script>
import translateForm from './components/translateForm'
import translateOutput from './components/translateOutput'

export default {
  name: 'App',
  data:function(){
    return{
      translatedText:""
    }
  },
  components: {
    translateForm, 
    translateOutput
  },
  methods:{
    translateText:function(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180405T020547Z.f227df74e59e0a32.0a0d0fa07d9f66d61c4be28eb467083d300d343e&lang='+language+'&text='+text+'')
      .then(function(responce){
        //console.log(responce.body.text[0]);
        this.translatedText=responce.body.text[0];
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app h1{ font-size: 350%; }
</style>

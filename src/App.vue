<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class='text-muted'>translated by Yandex (俄罗斯服务器,有点慢)</h5>
    <translateForm @formSubmit='translateText'></translateForm>
    <translateOutput v-text="textTranslated"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/translateOutput'

export default {
  name: 'App',
  data:function(){  //定义一个属性,用于存放 翻译后的内容
    return {
      textTranslated:''
    }
  },
  components: { //组件
    TranslateForm,
    TranslateOutput
  },
  methods:{ //方法
    translateText:function(text,lang){
      // alert(text)
      //得配个vue-resource使用
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180911T032104Z.acdf4dadd90d6039.0c52045dc97566522effce6abd29ede27075a577&lang='+lang+'&text='+text)
      .then((response)=>{
        // console.log(response.body.text[0])
        this.textTranslated = response.body.text[0] //存值
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
</style>

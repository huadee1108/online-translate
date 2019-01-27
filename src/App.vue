<template>
    <div class="container" id="app">
        <h1>在线翻译</h1>
        <h5 class="text-muted">简单 / 易用 /便捷</h5>
        <translate-form v-on:form-translate="translateText"></translate-form>
        <translate-output v-text="translatedText"></translate-output>
    </div>
</template>

<script>
    import TranslateForm from './components/TranslateForm'
    import TranslateOutput from './components/TranslateOutput'
    export default {
        name: "app",
        data:function(){
          return{
              translatedText: ""
          }
        },
        components:{
            TranslateForm,TranslateOutput
        },
        methods:{
            translateText:function (text,language) {
               this.axios.get('https://translate.yandex.net/api/v1.5/tr.json/translate?' +
                   'key=trnsl.1.1.20190127T140527Z.f11e7621a129706c.e20911bb07e4ea198c723e85f83928e3878565d1&' +
                   'lang='+language+'&text='+text)
                   .then((response) =>{
                       // console.log(response.data.text[0]);
                       this.translatedText = response.data.text[0];
                   })
            }
        }
    }
</script>

<style>
    #app{
        margin: 50px auto;
        color: #2c3e50;
    }
</style>

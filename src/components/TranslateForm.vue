<template>
    <div class="row" id="translateForm">
        <div class="col-md-6 col-md-offset-3">
            <form class="well form-inline" v-on:submit="formSubmit">
                <input class="form-control" type="text" v-model="textToTranslate" placeholder="请输入要翻译的内容"/>
                <select class="form-control" v-model="language">
                    <option value="en">English</option>
                    <option value="ru">Russian</option>
                    <option value="ko">korean</option>
                    <option value="ja">Janpenese</option>
                </select>
                <input class="btn btn-info" type="submit" value="翻译"/>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "translateForm",
        data:function(){
          return{
              textToTranslate: "",
              language: ""
          }
        },
        methods:{
            formSubmit:function (e) {
                // alert(this.textToTranslate);
                this.$emit("form-translate",this.textToTranslate,this.language);
                e.preventDefault();
            }
        },
        created:function () {
            this.language = "en";
        }
    }
</script>

<style scoped>

</style>

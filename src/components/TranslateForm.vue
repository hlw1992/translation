<template>
  <div id="translateForm">
      <!-- 居中样式 -->
      <div>
        <form class='bgform form-inline' @submit.prevent="formSubmit">
            <input type="text" class='form-control' placeholder="请输入中文" 
                v-model="textToTranslate">
            <select v-model="lang" class='form-control'>
                <option value="en">English</option>
                <option value="ja">Japanese</option>
                <option value="ko">Korean</option>
                <option value="fr">French</option>
            </select>
            <button class='btn btn-primary' type='submit'>翻译</button>
        </form>
      </div>
  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
      return {
          textToTranslate:"",
          //option下拉框 默认 显示英语
          lang:'en'
      }
  },
  methods:{
      formSubmit:function(e){
        //   alert(this.textToTranslate)
        // 向父组件传数据用 $emit, 参数可以多个
        this.$emit('formSubmit', this.textToTranslate, this.lang);
      }
  }
}
</script>

<style>
    .bgform{
        background-color: lightcyan;
        padding:20px;
        margin: 0 auto;
        width: 30%;
        min-width:400px;
        border: 1px solid lightgray;
        border-radius: 10px;
    }
</style>

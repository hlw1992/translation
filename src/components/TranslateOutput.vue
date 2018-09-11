<template>
    <h2 id="translateOutput">
        {{textTranslated}}
    </h2>
</template>

<script>


export default {
  name: 'translateOutput',
  //父组件 向 子组件传值 通过props数组
  props:[
      'textTranslated'
  ]
}
</script>

<style>
#translateOutput{
    margin-top:20px; 
}
</style>

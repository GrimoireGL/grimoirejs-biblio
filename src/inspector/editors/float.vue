<template lang="html">
  <div class="float-editor">
    <input type="text" v-model="attribute.value" v-on:input="changed"/>
  </div>
</template>

<script>
export default {
  props:["attribute"],
  methods:{
    changed:function(){
      if(this.isInt){
        this.attribute.value = Math.floor(this.attribute.value);
      }
      this.$store.commit("setMaterialAttribute",{
        name:this.attribute.name,
        value:this.attribute.value
      })
    }
  },
  computed:{
    isInt:function(){
      return this.attribute.type === "int";
    }
  }
}
</script>

<style lang="stylus">
.float-editor
  height 32px
  display flex
  flex-direction row-reverse
  input
    background-color rgba(0,0,0,0.1)
    outline none
    border solid 1px dimgray
    color white
    font-size 24px
    width 100px
</style>

<template lang="html">
  <div class="material-inspector">
    <MaterialHeader label="uniform variables"/>
    <Attribute v-for="uniform in uniforms" :attribute="uniform" isUniform="true"/>
    <MaterialHeader label="macro variables"/>
    <Attribute v-for="macro in macros" :attribute="macro" isUniform="false"/>

  </div>
</template>

<script>

import {mapState} from "vuex";
import MaterialHeader from "./header.vue";
import Attribute from "./attribute.vue";
export default {
  computed:{
    ...mapState(["uniforms","macros"])
  },
  components:{
    MaterialHeader,
    Attribute
  }
}
</script>

<style lang="stylus">
.material-inspector
  height 100%
</style>

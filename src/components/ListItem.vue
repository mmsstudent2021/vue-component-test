<template>
  <li v-on:dblclick="isEdit=true">

    <button @click="toDel">Del</button> &nbsp;

    <input
        v-if="isEdit"
        @keyup.enter="updateListTest"
        type="text"
        v-model="inputText">
    <span v-else>{{ listDetail.job }}</span>
  </li>
</template>

<script>
export default {
  props: {
    listDetail: Object,
  },
  data() {
    return {
      isEdit: false,
      inputText : this.listDetail.job
    }
  },
  methods: {
    updateListTest() {
      this.$emit('updateTest',this.inputText,this.listDetail.id)
      this.isEdit = false
    },
    toDel(){
      // console.log("to del list")
      this.$emit("delList",this.listDetail.id)
    }
  },
}
</script>

<style scoped>

</style>
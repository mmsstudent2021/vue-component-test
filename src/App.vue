<template>
  <div>

    <CardTitle title-text="Job List" />

    <ul>
      <ListItem
          v-for="list in lists"
          :key="list.id"
          :list-detail="list"
          @update-test="updateList"
          @del-list="del"
      />

    </ul>

  </div>
</template>

<script>
import ListItem from "@/components/ListItem";
import CardTitle from "@/components/CardTitle";
export default {
  components: {CardTitle, ListItem},
  data() {
    return {
      lists: [
        {
          id:1,
          job:"to eat",
          isDone : false
        },
        {
          id:2,
          job:"to sleep",
          isDone : true
        },
        {
          id:3,
          job:"to drink",
          isDone : false
        },
      ]
    }
  },
  methods: {
    updateList(x,y) {
      //finding index from list
      let currentIndex = this.lists.findIndex(list => list.id === y);
      console.log(currentIndex)
      //overwrite job property in lists[currentIndex]
      this.lists[currentIndex].job = x
    },
    del(x){
      // console.log("del form parent "+x)
      this.lists = this.lists.filter(list => list.id !== x)
    }
  },
}
</script>

<style scoped>

</style>
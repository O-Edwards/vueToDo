<template>
  <div>
    <h1> Vue To Do </h1>
    <v-form @submit.prevent="addToDo">
      <label for="to-do">
        To Do
      </label>
      <v-text-field id="new-todo" v-model="newToDo" />
      <v-btn type="submit" id="addButton">
        Add Item
      </v-btn>
    </v-form>
    <v-list :light=true v-if="toDoList.length >0" two-line>
      <template v-for="(item, index) in toDoList">
        <v-list-tile :key="item.title" @click="removeFromTodo(index)">
          <v-list-tile-content>
            <v-checkbox v-model="item.complete" />
            <v-list-tile-title>
              {{ item.title }}
            </v-list-tile-title>
            <!-- <v-btn @click="deleteToDo(item)">
              Remove
            </v-btn> -->
          </v-list-tile-content>
        </v-list-tile>
        <v-divider v-if="toDoList.length > 1" :key="index" />
      </template>
    </v-list>
  </div>
</template>

<script>
export default {
  components: {
  },
  data() {
    return {
      newToDo: '',
      toDoList: []
    }
  },
  methods: {
    addToDo() {
      this.toDoList.push({
        title: this.newToDo,
        complete: false
      })
    },
    removeFromTodo(index) {
      this.toDoList = this.toDoList.filter((item, idx) => {
        return idx !== index
      })
    },
    deleteToDo(toDo) {
      const idx = this.toDoList.indexOf(toDo)
      this.toDoList.splice(idx, 1)
    }
  }
}
</script>
<style>
</style>

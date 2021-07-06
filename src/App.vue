<template>
  <div>
    <div>
      <h2>List without tracking and without key</h2>
      <form @submit.prevent="addToUntrackedList">
        <input type="text" name="untrackedName" :placeholder="untrackedList[0]" />
        <button type="submit">Submit Name</button>
      </form>
      <ol>
        <!-- eslint-disable vue/require-v-for-key -->
        <li v-for="(li, i) in untrackedList">
          <input type="text">
          <button @click="deleteUntrackedItem(i)">Click to delete {{ li }}</button>
        </li>
      </ol>
    </div>
    <div>
      <h2>List with tracking using :key</h2>
      <form @submit.prevent="addToTrackedList">
        <input type="text" name="trackedName" :placeholder="trackedList[0]" />
        <button type="submit">Submit Name</button>
      </form>
      <ol>
        <li v-for="(li, i) in trackedList" :key="li">
          <input type="text">
          <button @click="deleteTrackedItem(i)">Click to delete {{ li }}</button>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {

    let untrackedList = []

    let trackedList = []

    return {
      untrackedList,
      trackedList
    }
  },
  methods: {
    addToUntrackedList(e) {
      this.untrackedList.push(e.srcElement[0].value)
    },
    addToTrackedList(e) {
      this.trackedList.push(e.srcElement[0].value)
    },
    deleteUntrackedItem(i) {
      console.log(i)
      this.untrackedList.splice(i, 1)
    },
    deleteTrackedItem(i) {
      this.trackedList.splice(i, 1)
    } 
  }
}
</script>

<style>

html, body {
  margin: 0;
  padding: 0
}

#app {
  inset: 0
}

</style>

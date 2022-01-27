<template>
  <div id="shopping-list">
    <div class="header">
      <h1>{{ header || 'Welcome' }}</h1>
      <button v-if="editing" @click="doEdit(false)" class="btn btn-cancel">Cancel</button>
      <button v-else @click="doEdit(true)" class="btn btn-primary">Add Item</button>
    </div>
    <div v-if="editing" class="add-item-form">
      <input @keyup.enter="saveItem" v-model="newItem" placeholder="Add an Item" />
      <label>
        <strong>High Priority</strong>
        <input type="checkbox" v-model="newItemHighPriority" />
      </label>
      <button @click="saveItem" class="btn btn-primary">Save Item</button>
    </div>
    <p v-if="items.length === 0">Nice job! You've bought all your items!</p>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.label }} | {{ item.priority }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ShoppingList',
  data() {
    return {
      header: 'Shopping List App',
      newItem: '',
      newItemHighPriority: false,
      editing: false,
      items: [
      ]
    }
  },
  methods: {
    saveItem() {
      this.items.push({ id: this.items.length + 1, label: this.newItem, priority: this.newItemHighPriority })
    },
    doEdit(editing) {
      this.editing = editing;
      this.nexItem = "";
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#shopping-list {
  width: 60%;
  padding: 2em;
  margin: 0 auto;
  background-color: whitesmoke;
  box-shadow: 0 4px 16px 2px #00000080;

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  border-radius: 12px;
}
h1 {
  color: #42b983;
}
</style>

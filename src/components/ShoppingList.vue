<template>
  <div id="shopping-list">
    <h1>{{ header || 'Welcome' }}</h1>
    <div class="add-item-form">
      <input v-model="newItem" placeholder="Add an Item" />
      <label>
        <strong>High Priority</strong>
        <input type="checkbox" v-model="newItemHighPriority" />
      </label>
      <button
        v-on:click="items.push({ id: items.length + 1, label: newItem, priority: newItemHighPriority })"
        class="btn btn-primary"
      >Save Item</button>
    </div>
    {{ newItem }} | {{ newItemHighPriority }}
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.label }} | {{ item.priority }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ShoppingList',
  /* eslint-disable */
  data() {
    return {
      header: 'Shopping List App',
      newItem: '',
      newItemHighPriority: false,
      items: [
        { id: 1, label: '10 party hats', priority: false },
        { id: 2, label: '2 board games', priority: false },
        { id: 3, label: '20 cups', priority: false },
      ]
    }
  }
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

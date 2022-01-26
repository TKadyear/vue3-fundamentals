<template>
  <div id="shopping-list">
    <h1>{{ header || 'Welcome' }}</h1>
    <form>
      <input v-model.trim="newItem" placeholder="Add an Item" />
      <label>
        <strong>High Priority</strong>
        <input type="checkbox" v-model="newItemHighPriority" />
      </label>
    </form>
    {{ newItem }} | {{ newItemHighPriority }}
    <form>
      <strong>Ice Cream Flavors</strong>
      <label>
        <input type="checkbox" v-model="iceCreamFlavors" value="vanilla" />
        Vanilla
      </label>
      <label>
        <input type="checkbox" v-model="iceCreamFlavors" value="chocolate" />
        Chocolate
      </label>
      <label>
        <input type="checkbox" v-model="iceCreamFlavors" value="strawberry" />
        Strawberry
      </label>
      <label>
        <input type="checkbox" v-model="iceCreamFlavors" value="Cookies-and-cream" />
        Cookies and Cream
      </label>
    </form>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.label }}</li>
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
      iceCreamFlavors: [],
      items: [
        { id: 1, label: '10 party hats' },
        { id: 2, label: '2 board games' },
        { id: 3, label: '20 cups' },
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

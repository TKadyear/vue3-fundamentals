<template>
  <div id="shopping-list">
    <div
      :class="['header text-center flex my-1', editing ? ' flex-row justify-between' : 'flex-col']"
    >
      <h1>{{ header || 'Welcome' }}</h1>
      <button v-if="editing" @click="doEdit(false)" class="btn btn-cancel">Cancel</button>
      <button v-else @click="doEdit(true)" class="btn btn-primary">Add Item</button>
    </div>
    <div v-if="editing" class="grid grid-colums gap-1 align-baseline">
      <label>
        <strong>High Priority</strong>
        <input type="checkbox" v-model="newItemHighPriority" />
      </label>
      <input @keyup.enter="saveItem" v-model="newItem" placeholder="Add an Item" />
      <p class="counter">{{ characterCount }}/200</p>
      <button :disabled="newItem.length < 5" @click="saveItem" s class="btn btn-primary">Save Item</button>
    </div>
    <p v-if="items.length === 0">Nice job! You've bought all your items!</p>
    <ul>
      <li
        v-for="item in items"
        @click="togglePurchased(item)"
        :key="item.id"
        :class="{ strikeout: item.purchased, 'high-priority': item.priority }"
      >{{ item.label }} | {{ item.priority }}</li>
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
        { id: 1, label: '10 party hats', priority: false, purchased: true },
        { id: 2, label: '2 board games', priority: false, purchased: true },
        { id: 3, label: '20 cups', priority: true, purchased: false },
      ]
    }
  },
  methods: {
    saveItem() {
      this.items.push({ id: this.items.length + 1, label: this.newItem, priority: this.newItemHighPriority, purchased: false })
    },
    doEdit(editing) {
      this.editing = editing;
      this.nexItem = "";
      this.newItemHighPriority = false;
    },
    togglePurchased(item) {
      console.log(item)
      item.purchased = !item.purchased
    }
  },
  computed: {
    characterCount() {
      return this.newItem.length;
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#shopping-list {
  @apply w-3/5 my-0 mt-16 mx-auto flex flex-col bg-slate-200 p-4 text-gray-800 rounded;
  box-shadow: 0 4px 16px 2px #00000080;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.grid-colums {
  grid-template-columns: 7em 1fr 2.5em 6em;
}
h1 {
  @apply font-bold text-xl text-green-900;
}
ul {
  @apply list-none;
}
ul > li {
  @apply cursor-pointer;
}
.strikeout {
  @apply line-through;
}
.high-priority {
  @apply text-red-900;
}
</style>

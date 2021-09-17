<template>
  <div class="container">
    <h2>Shopping list</h2>
    <div class="user-input">
      <input
        placeholder="Press enter to add new item"
        v-model="newItem"
      /><button @click="addItem()">Add item</button>
    </div>

    <ul>
      <li class="item" v-for="(item, n) in shoppingList" :key="n">
        {{ item }}
        <a class="button--remove" @click="deleteItem(item)">Remove</a>
      </li>
    </ul>

    <button class="button--delete" @click="removeAll()">Remove All</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: '',
      shoppingList: [],
    }
  },
  methods: {
    addItem() {
      this.shoppingList.push(this.newItem)
    },
    deleteItem(value) {
      this.shoppingList = this.shoppingList.filter(item => item !== value)
    },
    removeAll(){
      this.shoppingList = [];
    }
  },
}
</script>

<style lang="scss">
@import 'styles/global';

$color-green: #4fc08d;
$color-grey: #2c3e50;

.container {
  max-width: 600px;
  margin: 80px auto;
}

.item {
  display: flex;
  justify-content: space-between;
}

// Type
.h2 {
  font-size: 21px;
}

.user-input {
  display: flex;
  align-items: center;
  padding-bottom: 20px;
  input {
    width: 100%;
    padding: 10px 6px;
    margin-right: 10px;
  }
}

.item {
  display: flex;
  align-items: center;
}

// Buttons
button {
  appearance: none;
  padding: 10px;

  font-weight: bold;
  border-radius: 10px;
  border: none;
  background: $color-grey;
  color: white;
  white-space: nowrap;

  + button {
    margin-left: 10px;
  }
}

.button--delete {
  display: block;
  margin: 0 auto;
  background: red;
}

.button--remove {
  background: none;
  color: red;
  text-transform: uppercase;
  font-size: 11px;
  align-self: flex-end;
}

ul {
  display: block;
  margin: 0 auto;
  padding: 30px;
  border: 1px solid rgba(0, 0, 0, 0.25);

  > li {
    color: $color-grey;
    margin-bottom: 4px;
  }
}
</style>

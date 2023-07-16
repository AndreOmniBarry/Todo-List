<template>
  <div class="todo-list">
    <h1>Tasks</h1>
    <form @submit.prevent="addItem">
      <input type="text" v-model="newItem" placeholder="Add a new item">
      <button>Add Item</button>
    </form>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item }}
        <button @click="removeItem(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: '',
      items: []
    };
  },
  methods: {
    addItem() {
      if (this.newItem !== '') {
        this.items.push(this.newItem);
        this.newItem = '';
      }
    },
    removeItem(index) {
      this.items.splice(index, 1);
    }
  },
  scoped: {
    /* Styles for mobile devices */
    "@media (max-width: 480px)": {
      ".todo-list": {
        padding: "10px"
      },

      "input[type='text']": {
        width: "100%"
      },

      "button": {
        width: "100%",
        marginTop: "10px"
      },

      "li": {
        flexDirection: "column",
        alignItems: "flex-start"
      },

      "li button": {
        marginTop: "10px"
      }
    }
  }
};
</script>

<style scoped>
.todo-list {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

h1 {
  margin-top: 0;
}

form {
  margin-bottom: 20px;
}

input[type="text"] {
  padding: 5px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  padding: 5px 10px;
  font-size: 16px;
  background-color: #0066cc;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0052a3;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li:last-child {
  border-bottom: none;
}

li button {
  background-color: #cc0000;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

li button:hover {
  background-color: #a30000;
}
</style>
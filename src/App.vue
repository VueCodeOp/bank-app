<template>
  <div class="container">
    <h1 class="text-center mt-5 mb-5">My Bank App</h1>
    <div class="row mb-4">
    </div>

    <div class="col-8 offset-2 d-flex mt-4 justify-content-between">
      <input class="form-control" type="text" placeholder="add a new item" v-model="name"/>
      <input class="form-control" type="number" v-model="amount"/>
      <button class="btn btn-primary" @click="addItem" >Add</button>
    </div>

    <div>
      <ul class="mt-4 list-group">
        <li 
          v-for="({name, amount, id}) in items" :key="id" 
          class="list-group-item d-flex justify-content-between align-item-center"
        >
          <span>{{ name }}</span>
          <div>
            <span 
            :class="{
              'text-success': amount > 0, 
              'text-danger':amount < 0}" 
            > {{ amount }} €</span>
            <button class="btn btn-danger ms-3" @click="deleteItem(id)">Delete</button>
          </div>
          
        </li>
      </ul>  
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      items: [
        { id: 0, name: "Food", amount: -30 },
        { id: 1, name: "Groceries", amount: -42 },
        { id: 2, name: "Salary", amount: 130 },
      ],
      id: 3,
      amount: 0,
      name: ""
    };
  },
  methods: {
    addItem() {
      let newItem = {
        id: this.id,
        name: this.name,
        amount: this.amount
      };
      this.id++;
      this.items.push( newItem );
      console.log(this.items);
      this.name = "";
      this.amount = 0;
    },
    deleteItem(id) {
      console.log('delete clicado, item -> ' + id);
      this.items = this.items.filter(element => element.id !== id);
    },
  },
  computed: {
    income() {
    },
    expenses() {
    },
    balance() {
    },
  },
};
</script>

<style></style>

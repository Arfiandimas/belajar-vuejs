<template>
  <div id="app">
    <div class="container">
      <h1 class="mb-4">Daftar Pelanggan</h1>
      <hr>
        <CustomerTable 
          v-bind:customers='customers'
          @edit-customer='editCustomer'
          @delete-customer='deleteCustomer'
        />

        <CustomerForm 
          v-on:add-customer="addCustomer"
        />

    </div>
  </div>
</template>

<script>
import CustomerTable from './components/CustomerTable.vue'
import CustomerForm from './components/CustomerForm.vue'

export default {
  name: 'App',
  components: {
    CustomerTable,
    CustomerForm
  },
  data() {
    return {
      customers: [
        {
          id: 1,
          name: 'Bambang',
          email: 'bambang@mail.com',
          address: 'Jl.Kenanga',
        },
        {
          id: 2,
          name: 'Dika',
          email: 'dika@mail.com',
          address: 'Jl.Mangga',
        },
        {
          id: 3,
          name: 'Agus',
          email: 'agus@mail.com',
          address: 'Jl.Mataram',
        },
        {
          id: 4,
          name: 'Barjono',
          email: 'barjono@mail.com',
          address: 'Jl.Mataram',
        }
      ]
    }
  },
  methods: {
    addCustomer(customer) {
      this.customers.push(customer)
    },
    editCustomer(id, data) {
      this.customers = this.customers.map(function (customer) {
        return customer.id === id ? data : customer
      })
    },
    deleteCustomer(id) {
      this.customers = this.customers.filter(function (customer) {
        return customer.id !== id
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

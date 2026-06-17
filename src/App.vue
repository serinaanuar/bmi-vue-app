<template>
  <div id="app">

    <AppHeader />

    <div class="layout">

      <AppSidebar />

      <div class="main-content">
        <AddPersonView @add-person="addPerson" />

        <LastPersonView :lastPerson="lastPerson" />

        <PersonListView :persons="persons" @delete-person="deletePerson" />
      </div>
    </div>
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import AppSidebar from './components/AppSidebar.vue'

import AddPersonView from './views/AddPersonView.vue'
import LastPersonView from './views/LastPersonView.vue'
import PersonListView from './views/PersonListView.vue'

export default {
  name: 'App',

  components: {
    AppHeader,
    AppFooter,
    AppSidebar,
    AddPersonView,
    LastPersonView,
    PersonListView
  },

  data() {
    return {
      persons: []
    }
  },

  computed: {
    lastPerson() {
      if (this.persons.length === 0) {
        return null
      }
      return this.persons[this.persons.length - 1]
    }
  },

  methods: {
    addPerson(person) {
      this.persons.push(person)
    },

    deletePerson(index) {
      this.persons.splice(index, 1)
    }
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}

.header {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 20px;
}

.layout {
  display: flex;
  min-height: calc(100vh - 120px);
}

.sidebar {
  width: 200px;
  background-color: #ddd;
  padding: 20px;
}

.side-menu {
  list-style-type: none;
  padding: 0;
}

.menu-link {
  display: block;
  padding: 10px;
  text-decoration: none;
  color: #333;
}

.menu-link.active {
  background-color: #bbb;
}

.main-content {
  flex: 1;
  padding: 20px;
}

form {
  margin-bottom: 20px;
}

input {
  display: block;
  margin-bottom: 10px;
  padding: 8px;
  width: 200px;
}

button {
  padding: 8px 16px;
  background-color: #333;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #555;
}

.single {
  padding: 10px;
  background-color: #eee;
  margin-bottom: 20px;
}

.person-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}

.person-info {
  flex: 1;
}

.delete-btn {
  background: red;
  color: white;
  border: none;
  padding: 6px 12px;
  cursor: pointer;
  border-radius: 4px;
}

.delete-btn:hover {
  background: darkred;
}

ul {
  list-style-type: none;
  padding: 0;
}

.footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 10px;
}
</style>

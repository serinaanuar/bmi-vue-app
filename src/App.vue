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

/* HEADER */
.header {
  background-color: var(--primary);
  color: white;
  text-align: center;
  padding: 20px;
}

/* LAYOUT */
.layout {
  display: flex;
  min-height: calc(100vh - 120px);
}

/* SIDEBAR */
.sidebar {
  width: 200px;
  background-color: var(--surface-soft);
  padding: 20px;
  border-right: 3px solid var(--primary);
}

.side-menu {
  list-style: none;
  padding: 0;
}

.menu-link {
  display: block;
  padding: 10px;
  text-decoration: none;
  color: #333;
}

.menu-link.active {
  background-color: var(--primary);
  color: white;
}

/* MAIN */
.main-content {
  flex: 1;
  padding: 20px;
}

/* FORM */
form {
  margin-bottom: 20px;
}

input {
  display: block;
  margin-bottom: 10px;
  padding: 8px;
  width: 200px;
}

/* BUTTON - RED STYLE */
button {
  background-color: var(--primary);
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: var(--primary-dark);
}

/* BOX DISPLAY */
.single {
  padding: 10px;
  background-color: #eee;
  margin-bottom: 20px;
}

/* LIST */
ul {
  list-style: none;
  padding: 0;
}

li {
  padding: 10px;
  background-color: #fff;
  margin-bottom: 10px;
  border: 1px solid #ddd;
}

/* FOOTER */
.footer {
  background-color: var(--primary-dark);
  color: white;
  text-align: center;
  padding: 10px;
}
</style>

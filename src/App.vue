<template>
  <div id="app">

    <AppHeader />

    <div class="layout">

      <AppSidebar />

      <div class="main-content">
        <h2>BMI Calculator</h2>

        <PersonForm @add-person="addPerson" />

        <h2>Last Added Person</h2>
        <PersonCard
          v-if="lastPerson"
          :person="lastPerson"
        />

        <EmptyState
          v-else
          message="No person added yet."
        />

        <h2>Person List</h2>
        <ul v-if="persons.length > 0">
          <li v-for="(p, index) in persons" :key="index">
            <PersonCard :person="p" />
          </li>
        </ul>

        <EmptyState
          v-else
          message="No person in the list yet."
        />
        
      </div>
    </div>
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import AppSidebar from './components/AppSidebar.vue'
import PersonForm from './components/PersonForm.vue'
import PersonCard from './components/PersonCard.vue'
import EmptyState from './components/EmptyState.vue'
export default {
  name : 'App',
  components: {
    AppHeader,
    AppFooter,
    AppSidebar,
    PersonForm,
    PersonCard,
    EmptyState
  },
  data() {
    return {
      persons: [],
      lastPerson: null
    };
  },

  methods: {
    addPerson(person) {
    this.persons.push(person);
    this.lastPerson = person;
  },

    deletePerson(index) {
      this.persons.splice(index, 1);

      if (this.persons.length > 0) {
        this.lastPerson = this.persons[this.persons.length - 1];
      } else {
        this.lastPerson = null;
      }
    }
  }
};
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

ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 10px;
  background-color: #fff;
  margin-bottom: 10px;
  border: 1px solid #ddd;
}

.footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 10px;
}
</style>

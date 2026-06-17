<template>
  <div id="app">
    <AppHeader />

    <div class="layout">
      <AppSidebar />

      <div class="main-content">
        <AddPersonView @add-person="addPerson" />
        
        <LastPersonView :last-person="lastPerson" />
        
        <PersonListView
          :persons="persons"
          @delete-person="deletePerson"
        />
      </div>
    </div>

    <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppSidebar from './components/AppSidebar.vue'
import AppFooter from './components/AppFooter.vue'

import AddPersonView from './views/AddPersonView.vue'
import LastPersonView from './views/LastPersonView.vue'
import PersonListView from './views/PersonListView.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppSidebar,
    AppFooter,
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
      if (this.persons.length === 0) return null
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
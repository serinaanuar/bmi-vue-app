<template>
  <div>
    <h2>Person List</h2>

    <ul v-if="persons.length > 0">
    <li v-for="(p, index) in persons" :key="index" class="person-row">
  
    <div class="person-info">
        <PersonCard :person="p" />
    </div>

    <button class="delete-btn" @click="$emit('delete-person', index)">
        Delete
    </button>

    </li>
    </ul>

    <EmptyState
      v-else
      message="No person in the list yet."
    />
  </div>
</template>

<script>
import PersonCard from '../components/PersonCard.vue'
import EmptyState from '../components/EmptyState.vue'

export default {
  name: 'PersonListView',

  components: {
    PersonCard,
    EmptyState
  },

   emits: ['delete-person'],

  props: {
    persons: {
      type: Array,
      required: true
    }
  }

}
</script>
<template>
  <div>
    <h2>BMI Calculator</h2>

    <PersonForm @add-person="handleAdd" />
  </div>
</template>

<script>
import PersonForm from '../components/PersonForm.vue'

export default {
  name: 'AddPersonView',

  components: {
    PersonForm
  },

  emits: ['add-person'],

  methods: {
    handleAdd(person) {
      this.$emit('add-person', person)
    }
  }
}
</script>
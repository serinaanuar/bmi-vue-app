<template>
  <form @submit.prevent="submitForm">
    <input
      type="text"
      v-model="name"
      placeholder="Name"
      required
    >

    <input
      type="number"
      v-model.number="yob"
      placeholder="Year of Birth"
      required
    >

    <input
      type="number"
      v-model.number="weight"
      placeholder="Weight (kg)"
      required
    >

    <input
      type="number"
      v-model.number="height"
      placeholder="Height (cm)"
      required
    >

    <button type="submit">
      Add Person
    </button>
  </form>
</template>

<script>
export default {
  name: 'PersonForm',

  emits: ['add-person'],

  data() {
    return {
      name: '',
      yob: '',
      weight: '',
      height: ''
    }
  },

  methods: {
    submitForm() {
      const year = new Date().getFullYear()
      const age = year - this.yob

      const bmiValue =
        this.weight / ((this.height / 100) ** 2)

      const bmi = bmiValue.toFixed(2)

      let category = ''

      if (bmiValue < 18.5) {
        category = 'Underweight'
      } else if (bmiValue < 25) {
        category = 'Normal'
      } else {
        category = 'Overweight'
      }

      const person = {
        name: this.name,
        yob: this.yob,
        age: age,
        weight: this.weight,
        height: this.height,
        bmi: bmi,
        category: category
      }

      this.$emit('add-person', person)

      this.name = ''
      this.yob = ''
      this.weight = ''
      this.height = ''
    }
  }
}
</script>
<template>
  <div class="single">
    Name: {{ person.name }},
    Age: {{ person.age }},
    Weight: {{ person.weight }} kg,
    Height: {{ person.height }} cm,
    BMI: {{ person.bmi }},
    Category: {{ person.category }}
  </div>
</template>

<script>
export default {
  name: 'PersonCard',

  props: {
    person: {
      type: Object,
      required: true
    }
  }
}
</script>
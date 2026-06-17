<template>
  <div :class="listMode ? '' : 'single'">
    <span v-if="listMode">
      Name: {{ person.name }},
      Age: {{ person.age }},
      Weight: {{ person.weight }} kg,
      Height: {{ person.height }} cm,
      BMI: {{ person.bmi }}
    </span>

    <span v-else>
      Name: {{ person.name }},
      Age: {{ person.age }},
      Weight: {{ person.weight }} kg,
      Height: {{ person.height }} cm,
      BMI: {{ person.bmi }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'PersonCard',

  props: {
    person: {
      type: Object,
      required: true
    },

    listMode: {
      type: Boolean,
      default: false
    }
  }
}
</script>
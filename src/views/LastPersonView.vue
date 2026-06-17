<template>
	<div class="single">
		<div v-if="lastPerson">
			Name: {{ lastPerson.name }},
			Age: {{ lastPerson.age }},
			Weight: {{ lastPerson.weight }} kg,
			Height: {{ lastPerson.height }} cm,
			BMI: {{ lastPerson.bmi }},
			Category: {{ lastPerson.category }}
		</div>
		<div v-else>
			No person added yet.
		</div>
	</div>
</template>

<script>
export default {
	name: 'LastPersonView',
	props: {
		lastPerson: {
			type: Object,
			default: null
		}
	}
}
</script>


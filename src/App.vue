<template>
  <div id="app">
    <div class="header">
      <h1>BMI Application</h1>
      <p>Vue CLI Version</p>
    </div>

    <div class="layout">
      <div class="sidebar">
        <h3>Menu</h3>
        <ul class="side-menu">
          <li><a href="#" class="menu-link active">Add Person</a></li>
          <li><a href="#" class="menu-link">Last Added</a></li>
          <li><a href="#" class="menu-link">Person List</a></li>
        </ul>
      </div>

      <div class="main-content">
        <h2>BMI Calculator</h2>

        <form @submit.prevent="addPerson">
          <input type="text" v-model="name" placeholder="Name" required>
          <input type="number" v-model.number="yob" placeholder="Year of Birth" required>
          <input type="number" v-model.number="weight" placeholder="Weight (kg)" required>
          <input type="number" v-model.number="height" placeholder="Height (cm)" required>
          <button type="submit">Add Person</button>
        </form>

        <h2>Last Added Person</h2>
        <div class="single">
          <span v-if="lastPerson">
            Name: {{ lastPerson.name }},
            Age: {{ lastPerson.age }},
            Weight: {{ lastPerson.weight }} kg,
            Height: {{ lastPerson.height }} cm,
            BMI: {{ lastPerson.bmi }},
            Category: {{ lastPerson.category }}
          </span>
          <span v-else>
            No person added yet.
          </span>
        </div>

        <h2>Person List</h2>
        <ul v-if="persons.length > 0">
          <li v-for="(p, index) in persons" :key="index">
            {{ index + 1 }}.
            Name: {{ p.name }},
            Age: {{ p.age }},
            Weight: {{ p.weight }} kg,
            Height: {{ p.height }} cm,
            BMI: <strong>{{ p.bmi }}</strong>,
            Category: {{ p.category }}
            <button @click="deletePerson(index)">Delete</button>
          </li>
        </ul>
        <div v-else class="single">
          No person in the list yet.
        </div>
      </div>
    </div>

    <div class="footer">
      <p>© 2026 BMI App | Web Technology Course</p>
    </div>
  </div>
</template>

<script>
export default {
  name : 'App',
  components: {
    
  },
  data() {
    return {
      name: '',
      yob: '',
      weight: '',
      height: '',
      persons: [],
      lastPerson: null
    };
  },

  methods: {
    addPerson() {
      const yob = parseInt(this.yob);
      const weight = parseFloat(this.weight);
      const height = parseFloat(this.height);

      const year = new Date().getFullYear();
      const age = year - yob;

      const bmiValue = weight / ((height / 100) ** 2);
      const bmi = bmiValue.toFixed(2);

      let category = '';
      if (bmiValue < 18.5) {
        category = 'Underweight';
      } else if (bmiValue < 25) {
        category = 'Normal';
      } else {
        category = 'Overweight';
      }

      const person = {
        name: this.name,
        yob: yob,
        age: age,
        weight: weight,
        height: height,
        bmi: bmi,
        category: category
      };

      this.persons.push(person);
      this.lastPerson = person;

      this.name = '';
      this.yob = '';
      this.weight = '';
      this.height = '';
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

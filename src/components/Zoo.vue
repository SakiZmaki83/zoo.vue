<template>
  <div>
   <form @submit.prevent="addAnimal">

      <label>Vrsta</label>
      <input v-model="newAnimal.vrsta" type="text" placeholder="vrsta"/>

      <label>Ime</label>
      <input v-model="newAnimal.ime" type="text" placeholder="ime"/>
     

      <label>Datum rodjenja</label>
      <input v-model="newAnimal.datumRodjenja" type="text" placeholder="datum rodjenja"/>
      
      <button type="submit">add animal</button>
    </form>

  <table>

  <thead>
     <th>Vrsta</th>
     <th>Ime</th>
     <th>Datum rodjenja</th>
  </thead>

  <tbody>
  <tr v-for="(animal, key) in animals" :key="key">
     <td>{{ animal.vrsta }}</td>
     <td>{{ animal.ime }}</td>
    <td v-if="(animal.datumRodjenja) != ''">{{ animal.datumRodjenja }}</td>
    <td v-else > Nepoznat </td>
    <td>
          <button @click="removeAnimal(animal)">Remove</button>
    </td>

    <td>
        <button onclick="topFunction()" id="myBtn" title="Go to top">Move to top</button>
    </td>
  </tr>
  </tbody>
  </table>

     
    
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data(){
    return{
      animals: [
        { vrsta: 'sisar', ime: 'slon', datumRodjenja: 2015},
        { vrsta: 'gmizavac', ime: 'iguana', datumRodjenja: 2016 },
        { vrsta: 'ptica', ime: 'noj', datumRodjenja: 2010 },
        { vrsta: 'vodozemac', ime: 'zaba', datumRodjenja: ''},
        { vrsta: 'riba', ime: 'japanka', datumRodjenja: 2017}
      ],
      newAnimal: {
        vrsta: '',
        ime: '',
        datumRodjenja: ''
      }
    }
  },
  methods: {
    removeAnimal(animal) {
      this.animals.splice(this.animals.indexOf(animal), 1)
    },
    topFunction(){
      this.animals.unshift(this.animals.indexOf(animal), 1)
    },
    addAnimal() {
      this.animals.push(this.newAnimal)
      this.newAnimal = {}
    },
  }
}
</script>

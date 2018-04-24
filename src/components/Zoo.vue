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
    
     <th>&nbsp;</th>
     <th>&nbsp;</th>
     <th>Sektor</th>
    
     
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
        <button @click="topFunction(animal)" id="myBtn" title="Go to top">Move to top</button>
    </td>
  </tr>
  </tbody>
  </table>

  <table>
     <thead>
        <th>Sektor</th>
         <th>&nbsp;</th>
        <th>Povrsina</th>
     </thead>

     <tbody>
     <tr v-for="(sector, key) in sectors" :key="key">
        <td>{{ sector.name }}</td>
    <td>
        <button @click="showList()" >Vidi listu</button>
    </td>
        <td>{{ sector.povrsina }}</td>
        

     </tr>
   

     </tbody>
  </table>

     
    
  </div>
</template>

<script>
const sectors = [
  { name: 'vodene zivotinje', povrsina: 'akvarijum'},
  { name: 'kopnene zivotinje', povrsina: 'kavez'},
  { name: 'vk', povrsina: 'terarijum' }
];

export default {
  name: 'AnimalList',
  data(){
    return{
      sectors: sectors,
      animals: [
        { vrsta: 'sisar', ime: 'slon', datumRodjenja: 2015, sector: sectors[1]},
        { vrsta: 'gmizavac', ime: 'iguana', datumRodjenja: 2016, sector: sectors[2]},
        { vrsta: 'ptica', ime: 'noj', datumRodjenja: 2010, sector: sectors[1]},
        { vrsta: 'gmizavac', ime: 'zmija', datumRodjenja: '', sector: sectors[2]},
        { vrsta: 'riba', ime: 'japanka', datumRodjenja: 2017, sector: sectors[0]}
      ],
      newAnimal: {
        vrsta: '',
        ime: '',
        datumRodjenja: '',
        sector: ''
      }
    }
  },
  methods: {
    removeAnimal(animal) {
      this.animals.splice(this.animals.indexOf(animal), 1)
    },
    topFunction(animal){
      this.animals.splice(this.animals.indexOf(animal), 1);
      this.animals.unshift(animal)
    },
    addAnimal() {
      this.animals.push(this.newAnimal)
      this.newAnimal = {}
    },
    
  }
}
</script>

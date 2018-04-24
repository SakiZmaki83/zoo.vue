<template>
  <div>

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
     <td>{{ animal.datumRodjenja }}</td>
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
      ]
    }
  }
}
</script>

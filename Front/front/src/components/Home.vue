<template>
  <div>
    <table class=""> 
      <thead>
        <th>Nom</th>
        <th>Nombre du jour</th>
        <th>Taux journalier</th>
        <th>Salaire</th>
        <th>Action</th>
      </thead>
      <tbody>
        <tr v-for="employé in employés" :key="employé.numEmployé">
            <td>{{ employé.nom }}</td>
            <td>{{ employé.nbJours }}</td>
            <td>{{ employé.tauxJournalier }}</td>
            <td>{{ employé.salaire }}</td>
            <td><button>Modifier</button></td>
            <td><button>Supprimer</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'myHome',
  data() {
    return {
      employés: []
    }
    
  },
  mounted() {
    this.displayData();
  },
  methods: {
    displayData(){
        axios.get("http://localhost:3000/employe").then(response => {
          console.log(response.data)
          this.employés = response.data;
        }).catch(error => {
          console.error("Erreur..!", error);
        })
    }
  }
}
</script>

<style>
</style>

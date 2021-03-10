<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title><img src="/assets/img/logo-v.png" alt="" style="width: 5%"></ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large"><img src="/assets/img/logo-v.png" alt="" style="width: 10%"></ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-card>
        <h1 style="text-align:center;">Nombre de places par heure:</h1>
        <p style="text-align:center;">{{ infos.place}}</p>
      </ion-card>
      <ion-card>
        <h1 style="text-align: center;">Horaires:</h1>
        <ion-list style="margin-top: 5%;">
        <ion-item style="border-radius: 20px 20px 0% 0%;">
          <ion-label><h2>Lundi</h2><p>{{infos.ouverture}}h-{{infos.fermeture}}h</p></ion-label>
          <ion-label><h2>Mardi</h2><p>{{infos.ouverture}}h-{{infos.fermeture}}h</p></ion-label>
          <ion-label><h2>Mercredi</h2><p>{{infos.ouverture}}h-{{infos.fermeture}}h</p></ion-label>
          <ion-label><h2>Jeudi</h2><p>{{infos.ouverture}}h-{{infos.fermeture}}h</p></ion-label>
        </ion-item>
        <ion-item>
          <ion-label><h2>Vendredi</h2><p>{{infos.ouverture}}h-{{infos.fermeture}}h</p></ion-label>
          <ion-label><h2>Samedi</h2><p>{{infos.ouverture}}h-{{infos.fermeture}}h</p></ion-label>
          <ion-label><h2>Dimanche</h2><p>Fermé ❌</p></ion-label>
        </ion-item>
    </ion-list>
      </ion-card>
      <ion-card>
        <h1 style="text-align:center;">Adresse:</h1>
        <p style="text-align:center;">📍{{ infos.adresse}}</p>
      </ion-card>

    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonCard, IonList, IonItem, IonLabel } from '@ionic/vue';
import axios from 'axios';

export default  {
  name: 'Infos',
   data(){
    return{        
      infos: '',
      }
    },
  components: {IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonCard, IonList, IonItem, IonLabel },
  mounted(){
           axios.get('https://cryptic-eyrie-01643.herokuapp.com/api/infos')
           .then(response => {
            console.log(response)
            this.infos = response.data.infos
            console.log(this.infos)
          }).catch(error => {
            console.log(error.response)
          })
    },
}
</script>
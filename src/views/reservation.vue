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
      <ion-card-header>
        <ion-card-title style="text-align: center;">Réserve maintenant!<br><img src="/assets/img/logo-v.png" alt="" style="width: 20%"></ion-card-title>
      </ion-card-header>

      <ion-card-content>
        {{form.email}}
        {{form.date}}
      </ion-card-content>
    </ion-card>
        <form method="POST" @submit.prevent="reserve">
          <div class="reservation" style="margin-left: 5%; margin-right: 5%; text-align: center;">
            <ion-item style="border-radius: 20px 20px 0% 0%; margin-top: 10vh;">
              <ion-label>Email:</ion-label>
              <ion-input type="email" name="email" v-model="form.email"></ion-input>
            </ion-item>
            <ion-item>
              <ion-label>Date:</ion-label>
              <ion-input type="date" name="date" v-model="form.date"></ion-input>
            </ion-item>
            <ion-item style="border-radius: 0% 0% 20px 20px;">
              <ion-label>Heure:</ion-label>
              <ion-input type="time" name="time" step="3600" v-model="form.time"></ion-input>
            </ion-item>
            <ion-button color="warning" type="submit">Réserver</ion-button>
          </div>
      </form>
      
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel, IonInput, IonButton, IonCard, IonCardHeader, IonCardTitle, IonCardContent } from '@ionic/vue';
import axios from 'axios';


export default  {
  name: 'Reservation',
  data(){
    return{      
      form:{
        email: '',
        date: '',
        time: '',
      }  
      
      }
    },
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonItem, IonLabel, IonInput, IonButton, IonCard, IonCardHeader, IonCardTitle, IonCardContent },
  methods: {
    reserve(){

        console.log(JSON.stringify(this.form));
        axios({
          method: "post",
          url: "http://cryptic-eyrie-01643.herokuapp.com/api/reservation",
          data: JSON.stringify(this.form),
          headers: { "Content-Type": "application/json" }
          })
        .then(function (response) {
          //handle success
          console.log(response);
        })
        .catch(function (response) {
          //handle error
          console.log(response);
        });
      
    }
  }
}
</script>
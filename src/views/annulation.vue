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
        <ion-card-title style="text-align: center;">Voulez-vous annuler votre réservation?<br><img src="/assets/img/logo-v.png" alt="" style="width: 20%"></ion-card-title>
      </ion-card-header>

      <ion-card-content>
        <p v-if="msg.error" style="text-align: center; color: red; font-size: 20px">{{msg.error}}</p>
        <p v-if="msg.success" style="text-align: center; color: green; font-size: 20px"> {{msg.success}}</p>

      </ion-card-content>
    </ion-card>
        <form method="POST" @submit.prevent="annulation">
          <div class="reservation" style="margin-left: 5%; margin-right: 5%; text-align: center;">
            <ion-item style="border-radius: 20px 20px 20px 20px; margin-top: 10vh;">
              <ion-label position="floating">Numéro de réservation:</ion-label>
              <ion-input type="text" name="token" v-model="token"></ion-input>
            </ion-item>

            <ion-button color="warning" type="submit">Annuler</ion-button>
          </div>
      </form>
      
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel, IonInput, IonButton, IonCard, IonCardHeader, IonCardTitle, IonCardContent } from '@ionic/vue';
import axios from 'axios';



export default  {
  name: 'Annulation',
  data(){
    return{      
     token: '',
      msg: {
          error:'',
          success:'',
      }
      
      }
    },
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonItem, IonLabel, IonInput, IonButton, IonCard, IonCardHeader, IonCardTitle, IonCardContent },
  methods: {
    annulation(){
        if(this.token.length > 0){
             axios.get('https://cryptic-eyrie-01643.herokuapp.com/api/annulation/'+this.token)
           .then(response => {
            console.log(response)
            this.msg = response.data
            this.token =''
            console.log(this.msg)
          }).catch(error => {
            
            this.msg.error = error.response.data.error
            console.log(this.msg)
          })
        }
        else{
            this.msg.error = "Veuillez remplir le champs"
        }
       
    
  }
}
}

</script>
<template>
  <ion-page>
    <ion-tabs>
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="home" href="/tabs/home">
          <ion-icon :icon="homeOutline" />
          <ion-label>Accueil</ion-label>
        </ion-tab-button>
          
        <ion-tab-button tab="reservation" href="/tabs/reservation">
          <ion-icon :icon="gameControllerOutline" />
          <ion-label>Réservation</ion-label>
        </ion-tab-button>
        
        <ion-tab-button tab="infos" href="/tabs/infos">
          <ion-icon :icon="informationCircleOutline" />
          <ion-label>Infos</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script>
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage } from '@ionic/vue';
import { gameControllerOutline, homeOutline, informationCircleOutline } from 'ionicons/icons';

export default {
  name: 'Tabs',
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage },
  setup() {
    return {
      gameControllerOutline, 
      homeOutline, 
      informationCircleOutline,
    }
  }
}
</script>
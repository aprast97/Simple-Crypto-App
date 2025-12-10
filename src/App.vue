<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Data Crypto</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      
      <div class="header-container">
        <ion-button expand="block" class="btn-refresh" @click="loadData">
          REFRESH
        </ion-button>
      </div>

      <div class="crypto-list">
        
        <div class="crypto-row" v-for="coin in coins" :key="coin.id">
          
          <div class="col-center">
            <div class="label-text">Rank</div>
            <div class="value-text">{{ coin.rank }}</div>
          </div>

          <div class="col-left">
            <div class="label-text">{{ coin.name }}</div>
            <div class="value-text">{{ coin.symbol }}</div>
          </div>

          <div class="col-right">
            <div class="label-text">USD</div>
            <div class="value-text">{{ coin.price_usd }}</div>
          </div>

        </div>

      </div>

      <div v-if="coins.length === 0" class="loading-state">
        <p>Memuat data...</p>
      </div>

    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton } from '@ionic/vue';
import { ref, onMounted } from 'vue';

interface Coin {
  id: string;
  rank: number;
  symbol: string;
  name: string;
  price_usd: string;
}

const coins = ref<Coin[]>([]);

const loadData = async () => {
  try {
    const response = await fetch('https://api.coinlore.net/api/tickers/');
    const data = await response.json();
    coins.value = data.data;
  } catch (error) {
    alert("Gagal koneksi API");
  }
};

onMounted(() => {
  loadData();
});
</script>

<style scoped>
.header-container {
  padding: 10px;
  background-color: white;
}

.btn-refresh {
  --background: #0054e9; 
  font-weight: bold;
  margin: 0;
}

.crypto-list {
  display: flex;
  flex-direction: column;
}

.crypto-row {
  display: flex;
  justify-content: space-between;
  align-items: center; 
  background-color: #fff8e1;
  
  padding: 12px 16px; 
  
  border-bottom: 2px solid #e6dcb8; 
}

.col-center {
  width: 15%;
  display: flex;
  flex-direction: column;
  align-items: center; 
}

.col-left {
  width: 35%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.col-right {
  width: 50%;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  text-align: right;
}

.label-text {
  display: block; 
  font-size: 13px;
  color: #000000; 
  font-weight: 500;
  
  margin-bottom: 5px; 
  
  line-height: 1.1;
}

.value-text {
  display: block;
  font-size: 20px;
  color: #000000;
  font-weight: bold;
  line-height: 1.1;
}

.loading-state {
  text-align: center;
  padding: 20px;
  color: #000;
}
</style>
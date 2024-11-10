<template>
    <v-app class="app">
        <v-container fluid>
            <v-header>
                <v-toolbar class="header" :style="{ flexDirection: isMobile ? 'column' : 'row' }">
                    <v-toolbar-title class="logo">Pastas with Rodola</v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-btn text v-for="link in navLinks" :key="link.text" :href="link.href" v-if="!isMobile">{{ link.text }}</v-btn>
                    <v-btn class="start-now" text>Let's decide</v-btn>
                </v-toolbar>
            </v-header>
            <!-- Pasta Selection -->
            <div>
                <h5>Select Your Pasta</h5>
                <div class="pasta-images">
                    <div v-for="pasta in pastasList" :key="pasta.text" class="pasta-item">
                        <img :src="pasta.src" :alt="pasta.text" class="pasta-image" />
                        <p>{{ pasta.text }}</p>
                    </div>
                </div>
                <v-select v-model="selectedPasta" :items="pastaOptions" label="Choose Pasta"></v-select>
            </div>
            <!-- Sauce Selection -->
            <div>
                <h5>Select Your Sauce</h5>
                <v-select v-model="selectedSauce" :items="sauceOptions" label="Choose Sauce"></v-select>
            </div>
            <!-- Display Selection -->
            <div>
                <h5>Your Selection:</h5>
                <p>Pasta: {{ selectedPasta }}</p>
                <p>Sauce: {{ selectedSauce }}</p>
            </div>
        </v-container>
    </v-app>
</template>

<script setup>
import { ref, computed } from 'vue';

const navLinks = [
    { text: 'Recipies', href: '#' },
    { text: 'Shops', href: '#' },
    { text: "Jana's favourites", href: '#' }
];

const pastasList = [
    { text: 'Parppadelle', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314977/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Parpadelle_al_pepe_nero.jpg' },
    { text: 'Gnocchi', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314972/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Gnocchi_di_patata.jpg' },
    { text: 'Rigatoni', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314973/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Rigatone.jpg' },
    { text: 'Spaghetti', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314974/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Spaghetti.jpg' },
    { text: 'Tagliatelle', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314976/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Tagliatelle.jpg' }
]

const pastaOptions = ['Spaghetti', 'Penne', 'Fusilli', 'Tagliatelle'];

const sauceOptions = ['Marinara', 'Alfredo', 'Pesto', 'Carbonara'];

const selectedPasta = ref('');

const selectedSauce = ref('');

const isMobile = computed(() => {
    return window.innerWidth < 768;
});
</script>

<style scoped>
.app, .header {
    background-color: #eff7ff;
}

.logo {
    font-weight: bold;
    font-size: 24px;
    color: #6482AD;
}

.start-now {
    background-color: #6482AD;
    color: #fff;
    border-radius: 20px;
}

.pasta-images {
    display: flex;
    justify-content: space-around;
    margin-bottom: 10px;
}

.pasta-image {
    width: 50px; /* Adjust size as needed */
    height: 50px; /* Adjust size as needed */
    border-radius: 50%; /* Makes the image round */
    object-fit: cover; /* Ensures the image covers the area */
}

.pasta-item {
    display: flex;
    flex-direction: column; /* Stack image and name vertically */
    align-items: center; /* Center items horizontally */
}
</style>

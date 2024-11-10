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
            <div class="pasta-selection">
                <h5>Select Your Pasta</h5>
                <div class="pasta-images" @click="selectPasta">
                    <div v-for="pasta in pastasList1" :key="pasta.text" class="pasta-item" :class="{ selected: selectedPasta === pasta.text }">
                        <img :src="pasta.src" :alt="pasta.text" class="pasta-image" :class="{ 'pasta-image-selected': selectedPasta === pasta.text }" />
                        <p :class="{ 'bold-text': selectedPasta === pasta.text }">{{ pasta.text }}</p>
                    </div>
                </div>
                <div class="pasta-images" @click="selectPasta">
                    <div v-for="pasta in pastasList2" :key="pasta.text" class="pasta-item" :class="{ selected: selectedPasta === pasta.text }">
                        <img :src="pasta.src" :alt="pasta.text" class="pasta-image" :class="{ 'pasta-image-selected': selectedPasta === pasta.text }" />
                        <p :class="{ 'bold-text': selectedPasta === pasta.text }">{{ pasta.text }}</p>
                    </div>
                </div>
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

const pastasList1 = [
    { text: 'Parppadelle', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314977/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Parpadelle_al_pepe_nero.jpg' },
    { text: 'Gnocchi', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314972/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Gnocchi_di_patata.jpg' },
    { text: 'Rigatoni', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314973/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Rigatone.jpg' },
    { text: 'Spaghetti', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314974/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Spaghetti.jpg' },
    { text: 'Tagliatelle', src: 'https://res.cloudinary.com/hesvvq3zo/image/upload/v1724314976/CARTA/PASTA-TRADIZIONALE/12_Pasta_Tradizionale_Tagliatelle.jpg' },
    { text: 'Farfalle', src: 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/ac/Farfalle_Pasta.JPG/1024px-Farfalle_Pasta.JPG' },
]

const pastasList2 = [
    { text: 'Fusilli', src: 'https://zerostore.co.uk/wp-content/uploads/2020/12/image_887ba228-bcd1-4c04-8858-ed9b1a1ea83d.jpg' },
    { text: 'Penne', src: 'https://www.the-pasta-project.com/wp-content/uploads/Penne-Pasta-1.jpg' },
    { text: 'Orzo', src: 'https://www.hola.com/horizon/original_aspect_ratio/1d0242051cb2-orzo-interior-z.jpg?im=Resize=(960),type=downsize' },
    { text: 'Lumaconi', src: 'https://fiorfiore-italianfood.com/wp-content/uploads/2020/01/Pasta_Lumaconi_mobile.jpg' },
    { text: 'Chifferi', src: 'https://i.shgcdn.com/74600a26-66ea-40ba-8879-ab80225c3c46/-/format/auto/-/preview/3000x3000/-/quality/lighter/-/resize/900x/' },
    { text: 'Fettuccini', src: 'https://www.foodiecrush.com/wp-content/uploads/2013/02/Lemon-Fettuccine-Alfredo-foodiecrush.com11.jpg' },
]

const sauceOptions = ['Marinara', 'Alfredo', 'Pesto', 'Carbonara'];

const selectedPasta = ref('');

const selectedSauce = ref('');

const isMobile = computed(() => {
    return window.innerWidth < 768;
});

const selectPasta = (event) => {
    const pastaItem = event.target.closest('.pasta-item');
    if (pastaItem) {
        selectedPasta.value = pastaItem.querySelector('p').textContent;
    }
};
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

.pasta-selection {
    padding: 20px;
}

.pasta-images {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-bottom: 10px;
    height: 120px;
    align-items: center;
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
    width: 70px; /* Set a fixed width for the pasta item */
    height: 100px; /* Set a fixed height for the pasta item */
}

.pasta-image-selected {
    width: 70px; /* Adjust size for selected pasta */
    height: 70px; /* Adjust size for selected pasta */
}

.bold-text {
    font-weight: bold; /* Make text bold for selected pasta */
}
</style>

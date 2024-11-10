<template>
    <v-app class="app">
        <v-container fluid>
            <v-header>
                <v-toolbar class="header">
                    <v-toolbar-title class="logo">Pastas with Rodola</v-toolbar-title>
                    <v-spacer></v-spacer>
                </v-toolbar>
            </v-header>
            <!-- Pasta Selection -->
            <div>
                <h5>Select Your Pasta</h5>
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
import { ref } from 'vue';

const pastaOptions = ['Spaghetti', 'Penne', 'Fusilli', 'Tagliatelle'];
const sauceOptions = ['Marinara', 'Alfredo', 'Pesto', 'Carbonara'];

const selectedPasta = ref('');
const selectedSauce = ref('');
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
</style>

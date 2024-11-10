<template>
    <v-app class="app">
        <v-container fluid>
            <v-header>
                <v-toolbar class="header" :style="{ flexDirection: isMobile ? 'column' : 'row' }">
                    <v-toolbar-title class="logo">Title</v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-btn text v-for="link in navLinks" :key="link.text" :href="link.href" v-if="!isMobile">{{ link.text }}</v-btn>
                    <v-btn class="start-now" text>Log in</v-btn>
                </v-toolbar>
            </v-header>
        </v-container>
    </v-app>
</template>

<script setup>
import { ref, computed } from 'vue';

const navLinks = [
    { text: 'Home', href: '#' },
    { text: 'Profile', href: '#' },
    { text: 'Blog', href: '#' },
    { text: 'Forum', href: '#' },
    { text: 'Help!', href: '#' },
];

const isMobile = computed(() => {
    return window.innerWidth < 768; // Adjust the width as needed for your design
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
</style>

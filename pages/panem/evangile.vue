<template>
    <div class="bg-gray-100 py-10 min-h-screen">
        <div class="container mx-auto px-4">
            <!-- Page Title -->
            <h1 class="text-3xl font-bold text-gray-800 text-center mb-6">Évangile du Jour</h1>

            <!-- Date Picker -->
            <div class="text-center mb-6">
                <input type="date" id="date" v-model="selectedDate" @change="fetchEvangile"
                    class="border border-gray-300 rounded-lg p-2 mt-2" />
            </div>

            <!-- Loading State -->
            <div v-if="loading" class="text-center">
                <p class="text-gray-600">Chargement en cours...</p>
            </div>

            <!-- Error State -->
            <div v-if="error" class="text-center text-red-600">
                <p>Une erreur s'est produite : {{ error }}</p>
            </div>

            <!-- Evangile Content -->
            <div v-if="gospel" class="bg-white shadow-lg rounded-lg p-6">


                <h2 class="text-2xl font-semibold text-blue-600 mb-4">Évangile</h2>
                <h3 class="text-lg font-medium text-gray-800">{{ gospel.title }}</h3>
                <p class="italic mb-4 text-gray-600">Référence : {{ gospel.reference }}</p>
                <div class="text-gray-800" v-html="gospel.content"></div>

            </div>
            <div v-if="liturgicalInfo" class="bg-white shadow-lg rounded-lg p-6 mt-4">
                <h2 class="text-2xl font-semibold text-blue-600 mb-4">Informations liturgiques</h2>
                <ul class="list-disc list-inside mb-4 text-gray-800">
                    <li v-if="liturgicalInfo.tempsLiturgique">Temps liturgique : {{ liturgicalInfo.tempsLiturgique }}</li>
                    <li v-if="liturgicalInfo.fete">Fête : {{ liturgicalInfo.fete }}</li>
                </ul>
            </div>
        </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue';
import axios from 'axios';

// State Variables
const selectedDate = ref(new Date().toISOString().split('T')[0]); // Default: today's date
const liturgicalInfo = ref(null);
const gospel = ref(null);
const loading = ref(false);
const error = ref(null);

// Fetch Gospel Data
const fetchEvangile = async () => {
    loading.value = true;
    error.value = null;
    liturgicalInfo.value = null;
    gospel.value = null;

    try {
        const response = await axios.get(`https://api.aelf.org/v1/messes/${selectedDate.value}/afrique`);
        const data = response.data;

        // Liturgical Information
        liturgicalInfo.value = {
            date: data.informations.date,
            zone: data.informations.zone,
            tempsLiturgique: data.informations.temps_liturgique,
            fete: data.informations.fete,
        };

        // Gospel Content
        const gospelReading = data.messes[0].lectures.find(lecture => lecture.type === 'evangile');
        if (gospelReading) {
            gospel.value = {
                title: gospelReading.titre,
                reference: gospelReading.ref,
                content: gospelReading.contenu,
            };
        } else {
            error.value = "L'Évangile n'est pas disponible pour cette date.";
        }
    } catch (err) {
        error.value = err.message || "Impossible de récupérer les données.";
    } finally {
        loading.value = false;
    }
};

// Fetch Gospel on Page Load
fetchEvangile();
</script>
  
<style scoped>
/* Add any additional styles */
</style>
  
<template>
    <div class="bg-gray-100 py-10">
        <div class="container mx-auto px-4">
            <!-- Header Section -->
            <div class="bg-white shadow-lg rounded-lg p-6 mb-8">
                <h1 class="text-3xl font-bold text-gray-800">{{ pilgrimage.name }}</h1>
                <p class="text-gray-600 mt-2">{{ pilgrimage.description }}</p>
                <img src="/assets/cnpp.png" alt="Pilgrimage Image"
                    class="w-full h-64 object-cover mt-4 rounded-lg shadow-sm">
            </div>

            <!-- Filter Section -->
            <div class="bg-white shadow-lg rounded-lg p-6 mb-8">
                <h2 class="text-2xl font-semibold text-gray-800 mb-4">Filtrer par groupes de pélérins </h2>
                <select v-model="selectedGroup" class="w-full p-2 border border-gray-300 rounded-lg">
                    <option value="All">Tous les groupes</option>
                    <option v-for="group in groups" :key="group" :value="group">{{ group }}</option>
                </select>
            </div>

            <!-- Program of Events -->
            <div class="bg-white shadow-lg rounded-lg p-6 mb-8">
                <h2 class="text-2xl font-semibold text-gray-800 mb-4">Programmes</h2>
                <div v-if="filteredEvents.length === 0" class="text-gray-600">
                    Pas d'evenements pour ce groupe de pélerins
                </div>
                <div v-for="(event, index) in filteredEvents" :key="index" class="mb-8">
                    <!-- Event Details -->
                    <div class="mb-4">
                        <h3 class="text-lg font-medium text-blue-600">{{ event.name }}</h3>
                        <p class="text-gray-600">{{ event.time }}</p>
                        <p class="text-sm text-gray-500">Lieu : {{ event.lieu }}</p>
                        <p class="text-sm text-gray-500">Pélerins {{ event.group }}</p>
                    </div>
                    <!-- Event Map -->
                    <Map :latitude="event.location.lat" :longitude="event.location.lng" :popup="event.name" />

                </div>
            </div>
        </div>
    </div>
</template>
  
<script setup>
import { ref, computed } from 'vue';

// Dummy pilgrimage data
const pilgrimage = {
    name: "Pèlerinage Marial de Popenguine 2024",
    description: "Avec Marie notre Mère, marchons ensemble pour un Sénégal de Justice et de Paix.",
    image: "",
    events: [
        {
            name: "Messe du Matin",
            time: "8:00 - 9:00",
            group: "Classiques",
            lieu: "Basilique",
            location: { lat: 14.652, lng: -17.109 },
        },
        {
            name: "Confessions",
            time: "10:00 - 12:00",
            group: "Marcheurs",
            lieu: "Ancien sanctuaire",
            location: { lat: 14.653, lng: -17.110 },
        },
        {
            name: "Service de Guérison",
            time: "15:00 - 16:00",
            group: "Marcheurs",
            lieu: "Village des marcheurs",
            location: { lat: 14.654, lng: -17.108 },
        },
        {
            name: "Chapelet du Soir",
            time: "19:00 - 20:00",
            group: "Classiques",
            lieu: "Basilique",
            location: { lat: 14.651, lng: -17.107 },
        },
        {
            name: "Messe Dominicale",
            time: "10:00 - 11:00",
            group: "Marcheurs",
            lieu: "Nouveau sanctuaire",
            location: { lat: 14.650, lng: -17.111 },
        },
    ]

};

const groups = [...new Set(pilgrimage.events.map(event => event.group))];

const selectedGroup = ref("All");

// Filter events based on the selected group
const filteredEvents = computed(() => {
    if (selectedGroup.value === "All") {
        return pilgrimage.events;
    }
    return pilgrimage.events.filter(event => event.group === selectedGroup.value);
});
</script>
  
<style scoped>
/* Add additional styles if necessary */
</style>
  
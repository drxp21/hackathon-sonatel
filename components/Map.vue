<template>
    <iframe
        :src="`https://www.google.com/maps?q=${latitude},${longitude}&hl=fr-FR;z=14&output=embed`"
        height="120" style="width: 100%; border-radius: 10px" allowfullscreen="" loading="lazy">
    </iframe>
</template>
  
<script setup>
import { ref, onMounted } from 'vue';

defineProps(['latitude', 'longitude']);

</script>
  

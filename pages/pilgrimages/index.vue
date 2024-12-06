<template>
    <div class="bg-gray-100 py-10">
        <div class="container mx-auto px-4">
            <h1 class="text-3xl font-semibold text-center text-gray-800 mb-8">Pèlerinages</h1>
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
                <NuxtLink to="/pilgrimages/1" class="relative h-44 rounded-lg shadow-lg overflow-hidden bg-cover bg-center"
                    id="pel1">
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
                        <h2 class="text-white text-lg font-semibold text-center">
                            Pèlerinage Marial de Popenguine 2024
                        </h2>
                    </div>
                </NuxtLink>
                <NuxtLink to="/pilgrimages/1" class="relative h-44 rounded-lg shadow-lg overflow-hidden bg-cover bg-center"
                    id="pel2">
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
                        <h2 class="text-white text-lg font-semibold text-center">
                            Pèlerinage Marial des enfants 2024
                        </h2>
                    </div>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>

</script>

<style>
#pel1 {
    background-image: url('/assets/grotte.jpg');
    background-size: cover;
}

#pel2 {
    background-image: url('/assets/vierge.jpg');
    background-size: cover;
}
</style>

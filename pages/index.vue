<template>
    <div class="bg-gray-100 py-10 min-h-screen">
        <div class="container mx-auto px-4">
            <!-- Button Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <NuxtLink to="/pilgrimages" class="relative h-40 rounded-lg shadow-lg overflow-hidden group">
                    <img src="/assets/marche.jpg" alt="Panem Nostrum Quotidianium"
                        class="absolute inset-0 h-full w-full object-cover group-hover:scale-105 transition-transform" />
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center">
                        <h2 class="text-white text-lg font-semibold">Pèlerinages</h2>
                    </div>
                </NuxtLink>

                <NuxtLink to="/panem" class="relative h-40 rounded-lg shadow-lg overflow-hidden group">
                    <img src="/assets/panem.jpg" alt="Evangile du Jour"
                        class="absolute inset-0 h-full w-full object-cover group-hover:scale-105 transition-transform" />
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center">
                        <h2 class="text-white text-lg font-semibold">Pain de Vie</h2>
                    </div>
                </NuxtLink>

                <NuxtLink to="/panem" class="relative h-40 rounded-lg shadow-lg overflow-hidden group">
                    <img src="/assets/messe.jpg" alt="Evangile du Jour"
                        class="absolute inset-0 h-full w-full object-cover group-hover:scale-105 transition-transform" />
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center">
                        <h2 class="text-white text-lg font-semibold">Historique </h2>
                    </div>
                </NuxtLink>

            </div>
        </div>
    </div>
</template>
  
<script setup>
// No additional logic needed; buttons navigate to respective pages.
</script>

  
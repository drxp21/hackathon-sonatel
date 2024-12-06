<template>
    <div class="bg-gray-100 py-10 min-h-screen">
        <div class="container mx-auto px-4">
            <h1 class="text-3xl font-bold text-gray-800 text-center mb-8">Pain de vie</h1>

            <!-- Button Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Button: Evangile du Jour -->
                <NuxtLink to="/panem/evangile" class="relative h-40 rounded-lg shadow-lg overflow-hidden group">
                    <img src="/assets/liturgie.jpg" alt="Evangile du Jour"
                        class="absolute inset-0 h-full w-full object-cover group-hover:scale-105 transition-transform" />
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center">
                        <h2 class="text-white text-lg font-semibold">Évangile du Jour</h2>
                    </div>
                </NuxtLink>

                <!-- Button: Panem Nostrum Quotidianium -->
                <NuxtLink to="/panem/partages" class="relative h-40 rounded-lg shadow-lg overflow-hidden group">
                    <img src="/assets/confession.jpg" alt="Panem Nostrum Quotidianium"
                        class="absolute inset-0 h-full w-full object-cover group-hover:scale-105 transition-transform" />
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center">
                        <h2 class="text-white text-lg font-semibold">Panem Nostrum Quotidianium</h2>
                    </div>
                </NuxtLink>

                <!-- Button: Bible Numérique -->
                <NuxtLink to="/panem/bible" class="relative h-40 rounded-lg shadow-lg overflow-hidden group">
                    <img src="/assets/bible.jpg" alt="Bible Numérique"
                        class="absolute inset-0 h-full w-full object-cover group-hover:scale-105 transition-transform" />
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center">
                        <h2 class="text-white text-lg font-semibold">Bible Numérique</h2>
                    </div>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>
  
<script setup>
// No additional logic needed; buttons navigate to respective pages.
</script>

  
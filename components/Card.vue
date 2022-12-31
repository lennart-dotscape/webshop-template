<template>
    <div>
        <NuxtLink :to="'/products/' + data.id">
            <div class="overflow-hidden">
                <div class="transition duration-500 hover:scale-110">
                    <img :src="data.image" :alt="data.title">
                </div>
            </div>
        </NuxtLink>
        <div class="flex justify-between mt-2">
            <span class="font-bold mr-6">{{ data.title }}</span>
            <span>€{{ data.price }}</span>
        </div>
        <span class="text-gray-400">{{ data.category }}</span>
    </div>
</template>
<script setup>
    const props = defineProps({
        data: Object
    })
</script>
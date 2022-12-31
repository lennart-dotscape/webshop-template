<template>
    <div class="w-full hero bg-center bg-cover bg-no-repeat" :style="{ backgroundImage: 'url(' + data.image + ')'}">
        <div class="container h-full mx-auto flex flex-col items-center justify-center pt-24">
            <UiHeading :is="'h1'" :value="data.title" :size="'large'" :transform="'uppercase'" :color="'white'"/>
            <p class="w-3/4 text-white text-center mb-2 md:w-2/4">{{ data.description }}</p>
            <UiButton :is="'secondary'">Show products</UiButton>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>


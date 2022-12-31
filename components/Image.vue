<template>
    <div v-if="data.with_text" class="grid grid-cols-12 gap-6 gap-y-10 mt-4 items-center">
        <div class="col-span-12 lg:col-span-6" :class="data.text_align_left ? 'order-1' : 'order-2'">
            <UiHeading :is="'h2'" :value="data.title" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
            <p class="my-4">{{ data.description }}</p>
            <UiButton v-if="data.button_text" :to="data.button_url" :is="'primary'">{{ data.button_text }}</UiButton>
        </div>
        <div class="col-span-12 lg:col-span-6 order-1" :class="data.text_align_left ? 'order-2' : 'order-1'">
            <img :src="data.image" :alt="data.title">
        </div>
    </div>
    <div v-else class="grid grid-cols-12 gap-6 gap-y-10 mt-4">
        <div class="col-span-12">
            <img :src="data.image" :alt="data.title">
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>
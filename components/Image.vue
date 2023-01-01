<template>
    <div v-if="data.with_text && !data.text_in_image" class="grid grid-cols-12 gap-6 gap-y-10 mt-4 items-center">
        <div class="col-span-12 lg:col-span-6" :class="data.text_align_left ? 'lg:order-1' : 'lg:order-2'">
            <UiHeading :is="'h2'" :value="data.title" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
            <p class="my-4">{{ data.description }}</p>
            <UiButton v-if="data.button_text" :to="data.button_url" :is="'primary'">{{ data.button_text }}</UiButton>
        </div>
        <div class="col-span-12 lg:col-span-6 order-1" :class="data.text_align_left ? 'lg:order-2' : 'lg:order-1'">
            <div class="h-96 w-full">
                <img class="object-cover h-full w-full" :src="data.image" :alt="data.title">
            </div>
        </div>
    </div>
    <div v-else class="grid grid-cols-12 gap-6 gap-y-10 mt-4">
        <div class="col-span-12 relative">
            <div class="h-96 w-full">
                <img class="object-cover h-full w-full" :src="data.image" :alt="data.title">
            </div>
            <div v-if="data.text_in_image" class="absolute left-0 top-0 h-full w-full flex flex-col items-center justify-center text-center">
                <UiHeading :is="'h2'" :value="data.title" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
                <p v-if="data.description" class="my-4">{{ data.description }}</p>
                <UiButton v-if="data.button_text" :to="data.button_url" :is="'primary'">{{ data.button_text }}</UiButton>
            </div>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>
<template>
    <div class="grid grid-cols-12">
        <div class="col-start-3 col-span-8" :class="'text-' + data.text_align">
            <UiHeading :is="'h2'" :value="data.title" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
            <p class="my-4">{{ data.description }}</p>
            <UiButton v-if="data.button_text" :to="data.button_url" :is="'primary'">{{ data.button_text }}</UiButton>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>
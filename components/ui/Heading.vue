<template>
    <component :is="is" :class="[ 'text-' + color, transform, 'heading-' + size]">{{ value }}</component>
</template>

<script setup>
    const props = defineProps({
        is: String,
        value: String,
        color: String,
        transform: String,
        size: String
    })
</script>
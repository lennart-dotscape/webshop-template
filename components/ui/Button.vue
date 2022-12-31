<template>
    <NuxtLink to="/">
        <button :class="['button-' + is]">
            <slot />
        </button>
    </NuxtLink>
</template>

<script setup>
    const props = defineProps({
        is: String
    })
</script>
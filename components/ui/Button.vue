<template>
    <NuxtLink v-if="is_action" :to="to">
        <button :class="['button-' + is]">
            <slot />
        </button>
    </NuxtLink>
    <button v-else :class="['button-' + is]">
        <slot />
    </button>
</template>

<script setup>
    const props = defineProps({
        is: String,
        is_action: Boolean,
        link: String
    })
</script>
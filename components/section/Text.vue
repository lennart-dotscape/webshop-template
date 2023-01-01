<template>
    <section class="container mx-auto padding-vertical">
        <Text :data="data"/>
    </section>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>

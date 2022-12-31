<template>
    <section>
        <Hero :data="data"/>
    </section>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>

<template>
    <div class="container mx-auto padding-vertical">
        <CardOverview :data="data"/>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>
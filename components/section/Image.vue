<template>
    <div class="container mx-auto padding-vertical">
        <Image :data="data"/>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
</script>
<template>
    <UiHeading :is="'h2'" :value="data.title" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
    <div class="grid grid-cols-12 gap-6 gap-y-10 mt-4">
        <div v-for="product in products" :key="product.id" class="col-span-12 md:col-span-6 lg:col-span-4">
            <Card :data="product"/>
        </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        data: Object
    })
    const uri = 'https://api.npoint.io/89449da06a17dc19bc00/';
    const { data: products } = await useFetch(uri)
</script>
<template>
    <h1>{{ product.title }}</h1>
</template>

<script setup>
    const { id } = useRoute().params;
    const uri = 'https://api.npoint.io/89449da06a17dc19bc00/' + id
    const { data: product } = await useFetch(uri)
</script>

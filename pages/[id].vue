<template>
    <h1>{{ page.title }}</h1>
</template>

<script setup>
    const { id } = useRoute().params;
    const uri = 'https://api.npoint.io/8c1cf46069e5e6b92599/' + id
    const { data: page } = await useFetch(uri)
</script>

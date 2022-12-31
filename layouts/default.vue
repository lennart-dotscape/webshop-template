<template>
    <Header/>
        <div>
            <slot/>
        </div>
    <Footer/>
</template>

<script setup>
    const uri = 'https://api.npoint.io/c9cd68d38dfcfaafdb95/';
    const { data: pages } = await useFetch(uri)
</script>

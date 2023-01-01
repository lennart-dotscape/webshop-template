<template>
    <component v-for="section in sections" :key="section.id" :is="getSection(section.slug)" :data="section"/>
</template>

<script setup>
    const uri = 'https://api.npoint.io/8c1cf46069e5e6b92599/0/sections';
    const { data: sections } = await useFetch(uri)

    const SectionHero = resolveComponent('SectionHero')
    const SectionFaq = resolveComponent('SectionFaq')
    const SectionCardOverview = resolveComponent('SectionCardOverview')
    const SectionImage = resolveComponent('SectionImage')

    function getSection(slug) {
        switch(slug){
            case 'Hero':
                return SectionHero;
            case 'Faq':
                return SectionFaq;
            case 'CardOverview':
                return SectionCardOverview;
            case 'Image':
                return SectionImage;
        }
    }
</script>
<template>
    <div class="container mx-auto padding-vertical">
        <p class="my-1 text-sm uppercase">{{ page.title }}</p>
        <UiHeading :is="'h1'" :value="page.subtitle" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
        <p class="my-4">{{ page.description }}</p>
    </div>
    <component v-for="section in page.sections" :key="section.id" :is="getSection(section.slug)" :data="section"/>
</template>

<script setup>
    const { id } = useRoute().params;
    const uri = 'https://api.npoint.io/8c1cf46069e5e6b92599/' + id
    const { data: page } = await useFetch(uri)

    const SectionHero = resolveComponent('SectionHero')
    const SectionFaq = resolveComponent('SectionFaq')
    const SectionCardOverview = resolveComponent('SectionCardOverview')
    const SectionImage = resolveComponent('SectionImage')
    const SectionText = resolveComponent('SectionText')

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
            case 'Text':
                return SectionText;
        }
    }
</script>

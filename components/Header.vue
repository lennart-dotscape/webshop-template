<template>
    <header class="fixed top-0 bg-white w-full shadow-sm z-50">
        <nav class="container mx-auto flex justify-between py-8">
            <ul class="flex items-center">
                <li class="mr-12">
                    <NuxtLink to="/">
                        <img class="w-16" src="~/assets/img/logo_client.svg" alt="Logo client">
                    </NuxtLink>
                </li>
                <li v-for="page in pages" :key="page.id" class="mr-8 hidden lg:block">
                    <NuxtLink v-if="page.is_menu_item" :to="'/' + page.id" class="transition duration-200 hover:border-b-2 hover:border-black">{{ page.title }}</NuxtLink>
                </li>
            </ul>
            <ul class="flex flex-row items-center">
                <li class="mr-4 hidden lg:flex">
                    <UiButton :is="'primary'" :to="'/account'">My account</UiButton>
                </li>
                <li>
                    <NuxtLink to="/shopping-cart">
                        <svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M0 24C0 10.7 10.7 0 24 0H69.5c22 0 41.5 12.8 50.6 32h411c26.3 0 45.5 25 38.6 50.4l-41 152.3c-8.5 31.4-37 53.3-69.5 53.3H170.7l5.4 28.5c2.2 11.3 12.1 19.5 23.6 19.5H488c13.3 0 24 10.7 24 24s-10.7 24-24 24H199.7c-34.6 0-64.3-24.6-70.7-58.5L77.4 54.5c-.7-3.8-4-6.5-7.9-6.5H24C10.7 48 0 37.3 0 24zM128 464a48 48 0 1 1 96 0 48 48 0 1 1 -96 0zm336-48a48 48 0 1 1 0 96 48 48 0 1 1 0-96z"/></svg>
                    </NuxtLink>
                </li>
                <li class="flex lg:hidden ml-4">
                    <div @click="handleDrawer">
                        <svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path d="M0 96C0 78.3 14.3 64 32 64H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32C14.3 128 0 113.7 0 96zM0 256c0-17.7 14.3-32 32-32H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32c-17.7 0-32-14.3-32-32zM448 416c0 17.7-14.3 32-32 32H32c-17.7 0-32-14.3-32-32s14.3-32 32-32H416c17.7 0 32 14.3 32 32z"/></svg>
                    </div>
                </li>
            </ul>
        </nav>
    </header>
    <nav class="fixed inset-0 w-full h-full bg-white" ref="navigation_drawer" :class="is_drawer_open ? 'flex' : 'hidden'">
        <div class="container mx-auto pt-32 text-xl">
            <ul class="flex flex-col">
                <li v-for="page in pages" :key="page.id" class="mr-4 mb-4">
                    <NuxtLink v-if="page.is_menu_item" :to="'/' + page.id">{{ page.title }}</NuxtLink>
                </li>
            </ul>
            <ul class="flex flex-row items-center">
                <li class="mr-4">
                    <UiButton :is_action="true" :is="'primary'">My account</UiButton>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script setup>
    const uri = 'https://api.npoint.io/c9cd68d38dfcfaafdb95/';
    const { data: pages } = await useFetch(uri);

    const is_drawer_open = ref(false);

    function handleDrawer() {
        is_drawer_open.value = !is_drawer_open.value;
    }
</script>

<template>
   <div class="container mx-auto padding-vertical">
        <div class="grid grid-cols-12 gap-6 gap-y-10 mt-4">
            <div class="col-span-12 md:col-span-7">
                <ul>
                    <li v-for="product in shopping_cart" :key="product.id" class="flex flex-row border-b-2 border-black-400 mb-4 pb-4">
                        <div class="w-48 object-cover">
                            <img class="w-full" :src="product.product.image" :alt="product.title">
                        </div>
                        <div class="flex flex-row">
                            {{ product.size }}
                            <NuxtLink :to="'/products/' + product.product.id">{{ product.product.title }}</NuxtLink>
                            
                            {{ product.product.price }}
                        </div>
                    </li>
                </ul>
            </div>
            <div class="col-span-12 md:col-span-5">
                oke
                <span>{{ total_price }}</span>
            </div>
        </div>
    </div>
</template>

<script setup>
    const uri = 'https://api.npoint.io/89449da06a17dc19bc00/';
    const { data: products } = await useFetch(uri);

    const saved_products = ref(products)

    const shopping_cart = ref([]);

    onMounted(() => {
        let price = 0;
        (JSON.parse(localStorage.getItem('shopping_cart') || "[]")).forEach((item) => {
            saved_products.value.forEach((product) => {
                if(item.id == product.id) {
                    shopping_cart.value.push({product, size: item.size})
                }
            })
        })
    })
</script>
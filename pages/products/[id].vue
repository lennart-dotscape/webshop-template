<template>
    <div class="container mx-auto padding-vertical">
        <div class="grid grid-cols-12 gap-6 gap-y-10 mt-4">
            <div class="col-span-12 md:col-span-7">
                <div class="w-full object-cover">
                    <img class="w-full" :src="product.image" :alt="product.title">
                </div>
            </div>
            <div class="col-span-12 md:col-span-5">
                <div class="w-full">
                    <div class="mb-12">
                        <UiHeading :is="'h2'" :value="product.title" :size="'medium'" :transform="'uppercase'" :color="'black'"/>
                        <span class="text-lg mt-2 font-bold">€{{ product.price }}</span>
                    </div>
                    <span>Choose your size:</span>
                    <ul v-if="product.sizes" class="grid grid-cols-3 gap-2 gap-y-2">
                        <li v-for="size in product.sizes" :key="size" class="col-span-1 flex flex-grow">
                            <input class="hidden peer w-full" type="radio" :id="size.size" :value="size.size" name="size_select" :disabled="!size.available" v-model="product_form.size">
                            <label class="items-center justify-center flex w-full py-2 border-2 border-gray-300 cursor-pointer hover:border-gray-900 peer-checked:border-gray-900" :class="!size.available && 'bg-gray-100 text-gray-300 pointer-events-none'" :for="size.size" name="size_select">{{ size.size }}</label>
                        </li>
                    </ul>
                    <div v-if="product_form.id || product_form.size" class="flex flex-col mt-4">
                        <input type="text" class="hidden" :value="product.id" ref="product_id">
                        <UiButton :is="'primary'" @click="saveProduct">Add to shopping cart</UiButton>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    const { id } = useRoute().params;
    const uri = 'https://api.npoint.io/89449da06a17dc19bc00/' + id
    const { data: product } = await useFetch(uri)

    const product_id = ref('');
    const shopping_cart = ref([]);

    const product_form = ref(
        {
            "id": '',
            "size": '',
        }
    )

    onMounted(() => {
        shopping_cart.value = (JSON.parse(localStorage.getItem('shopping_cart') || "[]"))
    })

    function saveProduct() {
        product_form.value.id = id;
        shopping_cart.value.push(product_form.value)
        localStorage.setItem('shopping_cart', JSON.stringify(shopping_cart.value));
        product_form.value = {};
        window.location.href = '/shopping-cart'
    }
</script>

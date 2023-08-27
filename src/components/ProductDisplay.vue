<script>
    export default {
        name: 'ProductDisplay',
        data() {
            return {
                amount: 0,
                isAmountGreaterThan3: false,
                hasClickedCartButton: false,
                price: 75
            }
        },
        methods: {
            addToCart() {
                this.hasClickedCartButton = true
                this.isAmountGreaterThan3 = this.amount > 3
            }
        },
    }
</script>

<template>
    <div class="flex">
        <div class="flex w-1/2 h-screen bg-gray-200 items-center justify-center">
            <!-- thumbnail -->
            <img src="../assets/sofa-thumbnail.png" alt="">
        </div>
        <div class="flex flex-col justify-between w-1/2 h-screen p-12">
            <!-- detail -->
            <div class="">
                <h1 class="font-semibold text-4xl mb-2">Greyana Sofa</h1>
                <p>Introducing the Greyana Sofa. The perfect combination of style and comfort. With its sleek and modern design, this sofa is a statement piece that will elevate any living space. The Greyana Sofa features a stunning grey upholstery that is both soft to the touch and durable for everyday use. Crafted with a sturdy wooden frame and high-density foam cushions, the Greyana Sofa offers unbeatable comfort and support. The seat and back cushions are also removable and reversible, making it easy to maintain and keep looking like new.</p>
            </div>
            <div>
                <div class="text-4xl font-semibold">${{ price }}</div>
                <div class="flex justify-between w-28 items-center mt-4">
                    <button @click="amount--" class="bg-black text-white px-4 text-2xl disabled:bg-gray-500" :disabled="amount === 0">-</button>
                    <div class="px-6 bg-gray-200 h-full">{{ amount }}</div>
                    <button @click="amount++" class="bg-black text-white px-4 text-2xl">+</button>
                </div>
                <div v-if="hasClickedCartButton">
                    <div v-if="isAmountGreaterThan3" class="text-red-500 mt-1">maximum items that can be added is 3</div>
                    <div v-else class="text-green-500 mt-1">successfully added to cart</div>
                </div>

                <div class="mt-4">SubTotal: ${{ price * amount }}</div>
                <div class="flex gap-4 mt-10">
                    <button class="w-1/2 bg-black text-white py-5">Buy Now</button>
                    <button @click="addToCart()" class="w-1/2 bg-black text-white py-5">Add To Cart</button>
                </div>
            </div>
        </div>
        
    </div>
</template>
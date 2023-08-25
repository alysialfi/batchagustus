<script>
export default {
	name: "ProductDisplay",
	data() {
		return {
			amount: 0,
			isAmountValid: null,
			price: 75,
		};
	},
	methods: {
		addToCart() {
			this.isAmountValid = this.amount <= 3 && this.amount > 0;
			if (this.isAmountValid === true) {
				setTimeout(() => {
					this.isAmountValid = null;
				}, 1700);
			}
		},
	},

};
</script>

<template>
	<div class="flex">
		<div class="flex w-1/2 h-screen bg-gray-200 items-center justify-center">
			<!-- thumbnail -->
			<img
				src="../assets/sofa-thumbnail.png"
				alt=""
			/>
		</div>
		<div class="flex flex-col justify-between w-1/2 h-screen p-12">
			<!-- detail -->
			<div>
				<h1 class="font-semibold text-4xl mb-2">Greyana Sofa</h1>
				<p>
					Introducing the Greyana Sofa. The perfect combination of style and
					comfort. With its sleek and modern design, this sofa is a statement
					piece that will elevate any living space. The Greyana Sofa features a
					stunning grey upholstery that is both soft to the touch and durable
					for everyday use. Crafted with a sturdy wooden frame and high-density
					foam cushions, the Greyana Sofa offers unbeatable comfort and support.
					The seat and back cushions are also removable and reversible, making
					it easy to maintain and keep looking like new.
				</p>
			</div>
			<div>
				<div class="text-4xl font-semibold">${{ price }}</div>
				<div
					class="flex justify-between h-8 w-36 items-center mt-4 border-2 border-black"
				>
					<button
						@click="amount--"
                        :disabled="amount <= 0"
						class="bg-black text-white px-3 text-2xl block"
					>
						-
					</button>
					<div class="w-full text-center leading-[2rem] bg-gray-200 h-full">
						{{ amount }}
					</div>
					<button
						@click="amount++"
						class="bg-black text-white px-3 text-2xl block"
					>
						+
					</button>
				</div>
				<div
					v-if="isAmountValid === false"
					class="text-red-500 mt-1"
				>
					maximum items that can be added is 3
				</div>
				<div
					v-if="isAmountValid === true"
					class="text-green-500 mt-1"
				>
					successfully added to cart
				</div>

				<div class="mt-4">SubTotal: ${{ price * amount }}</div>
				<div class="flex gap-4 mt-10">
					<button class="w-1/2 bg-black text-white py-5">Buy Now</button>
					<button
						@click="addToCart()"
						class="w-1/2 bg-black text-white py-5"
					>
						Add To Cart
					</button>
				</div>
			</div>
		</div>
	</div>
</template>

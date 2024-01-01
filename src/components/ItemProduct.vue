<template>
    <div class="upper-top">

        <div class="product-card" v-if="product.category === `men's clothing` || product.category === `women's clothing`">
            <img :src="product.image" alt="product image" class="product-image" />

            <div class="container">
                <h1 class="tittle">
                    {{ product.title }}
                </h1>

                <div class="head-description">
                    <div class="category">
                        <p> {{ product.category }}</p>
                    </div>

                    <div class="rating">
                        <span style="margin-right: 5px;">{{ product.rating.rate }}/5</span>
                        <span v-for="n in 5" :key="n">
                            <span class="rating-rated" v-if="n <= product.rating.rate"></span>
                            <span class="rating-unrated" v-else></span>
                        </span>
                    </div>
                </div>

                <p class="description">
                    {{ product.description }}
                </p>

                <div class="price">${{ product.price }}</div>

                <div class="button-product">
                    <button class="buy-now">Buy now</button>
                    <button class="next-product" @click="fetchProduct">Next product</button>
                </div>
            </div>
        </div>

        <div class="product-card product-unavailable" v-else>

            <p>This product is unavailable to show</p>
            <button class="next-product" @click="fetchProduct">Next product</button>

        </div>

        <div class="upper"></div>

    </div>
</template>

<script>
export default {
    props: {
        product: Object,
    },

    methods: {
        fetchProduct() {
            this.$emit("fetch-product");
        }
    }
};
</script>

<style scoped src="../assets/css/style.css"></style>

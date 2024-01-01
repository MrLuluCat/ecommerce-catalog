<template>
    <div class="upper-top">
        <div v-if="loading" class="product-card loader-overlay">

            <div class="loader"></div>

        </div>
        <div class="else-loader" v-else>
            <div class="product-card"
                v-if="product.category === `men's clothing` || product.category === `women's clothing`">
                <img :src="product.image" alt="product image" class="product-image" />

                <div class="container">
                    <h1 class="tittle"
                        :class="{ menTextColor: product.category === `men's clothing`, womenTextColor: product.category === `women's clothing` }">
                        {{ product.title }}
                    </h1>

                    <div class="head-description">
                        <div class="category">
                            <p> {{ product.category }}</p>
                        </div>

                        <div class="rating">
                            <span style="margin-right: 5px;">{{ product.rating.rate }}/5</span>
                            <span v-for="n in 5" :key="n">
                                <div class="rating-rated"
                                    :class="{ menRatingRated: product.category === `men's clothing`, womenRatingRated: product.category === `women's clothing` }"
                                    v-if="n <= product.rating.rate"></div>
                                <div class="rating-rated"
                                    :class="{ menRatingUnrated: product.category === `men's clothing`, womenRatingUnrated: product.category === `women's clothing` }"
                                    v-else></div>
                            </span>
                        </div>
                    </div>

                    <p class="description">
                        {{ product.description }}
                    </p>

                    <div class="price"
                        :class="{ menTextColor: product.category === `men's clothing`, womenTextColor: product.category === `women's clothing` }">
                        ${{ product.price }}
                    </div>

                    <div class="button-product">
                        <button class="buy-now"
                            :class="{ menBuyButton: product.category === `men's clothing`, womenBuyButton: product.category === `women's clothing` }">Buy
                            now</button>
                        <button class="next-product"
                            :class="{ menNextButton: product.category === `men's clothing`, womenNextButton: product.category === `women's clothing` }"
                            @click="fetchProduct">Next product</button>
                    </div>
                </div>
            </div>

            <div class="product-card product-unavailable" v-else>

                <p>This product is unavailable to show</p>
                <button class="next-product" @click="fetchProduct">Next product</button>

            </div>
        </div>


        <div class="upper"
            :class="{ menColor: product.category === `men's clothing`, womenColor: product.category === `women's clothing`, defaultColor: product.category !== `men's clothing` && product.category !== `women's clothing` }">
        </div>



    </div>
</template>

<script>
export default {
    props: {
        product: Object,
    },

    data() {
        return {
            loading: false,
        };
    },

    methods: {
        fetchProduct() {

            this.loading = true;

            setTimeout(() => {
                this.$emit("fetch-product");

                this.loading = false;

            }, 1000);
        }
    }
};
</script>

<style scoped src="../assets/css/style.css"></style>

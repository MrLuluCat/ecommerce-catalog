<template>
    <div class="product">
        <h2>{{ product.title }}</h2>
        <p>{{ product.description }}</p>
        <p>Price: {{ product.price }}</p>
    </div>
</template>

<script>
export default {
    props: {
        product: Object,
    },
};
</script>

<style scoped>
.product {
    /* Desain produk di sini */
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    background-color: #f9f9f9;
}
</style>

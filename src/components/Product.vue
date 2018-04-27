<template>
    <div id="product">
        <p>{{title}}</p>
        <p>${{formatPrice(price)}}</p>
        <p>{{description}}</p>
    </div>
</template>

<script>
    export default {
        name: 'Product',
        props: {
            price: Number,
            title: String,
            description: String,
        },

        methods: {
            formatPrice: function(price){
               if(price <= 9){
                   price = `0${price}`
               }
               price = `${price}.00`;
                return price;
            },
        }
    }
</script>


<style>
    #product {
        flex-grow: 3;
        width: 33%;
        max-width: 33%;
        height: auto;
        border: 1px solid black;
        margin: 1px;
    }
</style>

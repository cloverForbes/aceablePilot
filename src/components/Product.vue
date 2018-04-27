<template>
    <div>
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

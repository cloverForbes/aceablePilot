<template>
    <div>
        <p>{{title}}</p>
        <p>{{price}}</p>
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
        }
    }
</script>

<template>
    <div>
        <h1>Robot Piloting Classes</h1>
        <Product
          v-for="product in products"
          v-bind:key="product.id"
          v-bind:title="product.title"
          v-bind:description="product.description"
          v-bind:price="product.price"
        ></Product>
        <br/>
    </div>
</template>

<script>
    import Product from './Product';

    export default {
        name: 'Container',
        data: () => (
            {
                products: []
            }
        ),
        components: {
            Product
        },

        methods: {
        },

        beforeMount(){
            fetch('https://mkt-endpoint.now.sh/products')
                .then(response => response.json())
                .then(data => {
                    this.products = data;
                })
        }
    }
</script>

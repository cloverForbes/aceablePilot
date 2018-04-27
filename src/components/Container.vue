<template>
    <div>
        <h1>Robot Piloting Classes</h1>
        <div id="productContainer">
            <Product
                    v-for="product in products"
                    v-bind:key="product.id"
                    v-bind:title="product.title"
                    v-bind:description="product.description"
                    v-bind:price="Number(product.price)"
            ></Product>
        </div>
        <br/>
    </div>
</template>

<script>
    import Product from './Product';

    export default {
        name: 'Container',
        data: () => (
            {
                products: [],
                sortBy: 'price',
            }
        ),
        components: {
            Product
        },

        methods: {
            sortData: function(){
                let sort = this.sortBy;
                this.products.sort((a,b) => {
                    if(a[sort] > b[sort]){
                        return 1;
                    }
                    if(a[sort] < b[sort]){
                        return -1;
                    }
                    return 0;
                })
            },
        },

        beforeMount(){
            fetch('https://mkt-endpoint.now.sh/products')
                .then(response => response.json())
                .then(data => {
                    this.products = data;
                    this.sortData();
                })
        }
    }
</script>

<style>
    #productContainer{
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        width: 100%;
    }
    body{
        text-align: center;
    }
</style>

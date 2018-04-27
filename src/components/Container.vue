<template>
    <div>
        <div id="container">
            <img id="logo" src="../assets/logo.png">
            <h1>Robot Piloting Classes</h1>
        </div>
        <div id="form">
            <input v-on:change="sortData()" type="radio" id="title" value="title" v-model="sortBy">
            <label for="title">Title</label>
            <br>
            <input v-on:change="sortData()" type="radio" id="price" value=price v-model="sortBy">
            <label for="price">Price</label>
            <i v-on:click="reverse()">{{asc ? '▲' : '▼'}}</i>
        </div>
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
                asc: true,
            }
        ),
        components: {
            Product
        },

        methods: {
            sortData: function(){
                let sort = this.sortBy;
                this.products.sort((a,b) => {
                    let aSort = a[sort];
                    let bSort = b[sort];
                    if(!(isNaN(aSort))){
                        aSort = Number(aSort);
                        bSort = Number(bSort);
                    }
                    if(aSort > bSort){
                        return 1;
                    }
                    if(aSort < bSort){
                        return -1;
                    }
                    return 0;
                })
            },

            reverse: function(){
                this.asc = !this.asc;
                this.products.reverse();
            }
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

    #logo{
        height: 50px;
        max-width: 200px;
        flex-grow: 2;
    }

    #container{
        display: flex;
    }

    h1 {
        flex-grow: 2;
        color: #00BEC4;
    }

    i {
        position: absolute;
        top: 16%;
    }
</style>

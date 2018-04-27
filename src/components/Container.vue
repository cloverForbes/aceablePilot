<template>
    <div>
        <h1>Robot Piloting Classes</h1>
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
        }
    }
</script>

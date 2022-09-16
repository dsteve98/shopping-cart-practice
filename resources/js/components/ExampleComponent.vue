<template>
    <div class="container">
        <products-section
            v-model="products"
        />
        <cart v-model="products"></cart>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                products: [
                    {
                        id: 'cc919e21-ae5b-5e1f-d023-c40ee669520c',
                        name: 'Indomie Goreng Rendang',
                        description: 'Masakan instan terenak di dunia',
                        stock: 10,
                        price: 3900,
                        qty: 0,
                    },
                    {
                        id: 'bcd755a6-9a19-94e1-0a5d-426c0303454f',
                        name: 'Mie Gelas Rendang',
                        description: 'Mie instant khusus anak kosan',
                        stock: 5,
                        price: 1500,
                        qty: 0,
                    },
                    {
                        id: '727026b7-7f2f-c5a0-ace9-cc227e686b8e',
                        name: 'Bakmi mewah ',
                        description: 'Kalau anak kosan jangan macam2 deh',
                        stock: 80,
                        price: 10000,
                        qty: 0,
                    }
                ],
                length: 2,
            }
        },
        computed:{
            
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>

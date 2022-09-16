<template>
	<div>
		<h1 class="title">Semua Produk</h1>
    	<table class="table">
		    <thead>
		      <tr>
		        <th>Name</th>
		        <th>Description</th>
		        <th>Stock</th>
		        <th>Price</th>
		        <th></th>
		      </tr>
		    </thead>
		    <tbody>
		      <tr v-for="(product, index) in input_products" track-by="id" :key="index">
		        <td>{{product.name}}</td>
		        <td>{{product.description}}</td>
		        <td>{{product.stock}}</td>
		        <td>Rp. {{product.price}}</td>
		        <td class="no-pad"><button v-if="product.stock > 0" class="btn btn-primary" @click='addToCart(index)'>Add to cart</button></td>
		      </tr>
		    </tbody>
		</table>
	</div>
</template>

<script>

export default {
	methods: {
		addToCart: function(index){
			if(this.input_products[index].stock > 0){
				this.input_products[index].qty++
				this.input_products[index].stock--
			}
		}
	},
	props:{
		value:{
			type: Array,
			default: () => {
				return []
			}
		}
	},
	computed:{
      input_products: {
        get() {
          return this.value;
        },
        set(val) {
          this.$emit('input', val);
        }
      },
	}
}
</script>

<style scoped>
.no-pad{
	padding: 0px;
}
tr td{
	height: 45px !important;
	vertical-align: middle;
}
</style>

<template>
  <div class="cart">
    <h1 class="title">Keranjang Belanja</h1>
    <p v-show="!input_products.length">
    	<i>Your cart is empty!</i>
    </p>
    <table class="table" v-show="input_products.length">
    	<thead>
    		<tr>
    			<th style="width:25%">Name</th>
    			<th style="width:25%">Quantity</th>
    			<th style="width:25%">Price</th>
    			<th style="width:25%"></th>
    		</tr>
    	</thead>
    	<tbody>
    		<tr v-for="(p,index) in input_products" :key="index">
				<template v-if="p.qty > 0">
        		<td>{{ p.name }}</td>
        		<td>{{ p.qty }}</td>
        		<td>Rp. {{ p.price * p.qty }}</td>
        		<td class="no-pad"><button class="btn btn-danger" @click="removeItem(index)">Delete</button></td>
				</template>
        	</tr>
        	<tr>
        		<td><b>Total:</b></td>
        		<td></td>
        		<td><b>Rp. {{ total }}</b></td>
        	</tr>
    	</tbody>

    </table>
    <p><button v-show="input_products.length" class='btn btn-success' @click='checkout'>Checkout</button></p>
  </div>
</template>

<script>

export default {
	data(){
    	return {
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
  computed: {
    total () {
      return this.input_products.reduce((total, p) => {
        return total + p.price * p.qty
      }, 0)
    },
	input_products: {
		get() {
			return this.value;
		},
		set(val) {
			this.$emit('input', val);
		}
	},
  },
  methods: {
	removeItem:function(index){
		let temp = this.input_products[index].qty
		this.input_products[index].qty = 0
		this.input_products[index].stock += temp
	},
  	checkout(){
  		alert('Pay us Rp' + this.total)
  	}
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
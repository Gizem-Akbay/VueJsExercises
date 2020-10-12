<template>
    <div v-if="products.length > 0" class="row product-container">
        <h3 class="text-center">List of Added Products</h3>
        <hr>
        <div class="row product-container">
            <appProduct v-for="(product, index) in products" :key="index">
                <img class="card-img-top text-center mb-3" :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage">
                <div class="card-body">
                    <h5 class="card-title"> {{ product.title }} </h5>
                    <small><strong>Count : </strong> {{ product.count }}</small>
                    <br>
                    <small><strong>Price : </strong> {{ product.price }}</small>
                    <br>
                    <small><strong>Total : </strong> {{ product.totalPrice }}</small>
                </div>
            </appProduct>
        </div>
    </div>
</template>

<script>
import {eventBus} from "../main";
import Product from "./Product";
export default {
    components: {
        appProduct: Product
    },
    data() {
        return {
            products: [],
        }
    },
    created() {
        eventBus.$on("AddedProduct",(product) => {
            if(this.products.length < 10){
                this.products.push(product);
                eventBus.$emit("updatedProgBar",this.products.length);
            }
            else{
                alert("Doldu.");
            }
        })
    }
}
</script>

<style>
    
</style>

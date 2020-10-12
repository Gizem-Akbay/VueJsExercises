<template>
    <div class="col-md-5">
        <div class="col-md-11 card">
            <div class="card-body">
                <div class="form-group">
                    <label>Name of the product</label>
                    <input type="text" v-model="product.title" class="form-control" placeholder="adını giriniz">
                </div>
                <div class="row">
                    <div class="form-group col-md-6">
                        <label>Number of products</label>
                        <input type="text" v-model="product.count" class="form-control"
                            placeholder="adetini giriniz">
                    </div>
                    <div class="form-group col-md-6">
                        <label>Product price</label>
                        <input type="text" v-model="product.price" class="form-control"
                            placeholder="fiyatını giriniz">
                    </div>
                </div>
                <button @click="addProduct()" class="btn btn-outline-info btn-block">Add</button>
            </div>
        </div>
    </div>
</template>

<script>
    import {eventBus} from "../main";
    export default {
        data() {
            return {
                product: { 
                    title: null,
                    count: null,
                    price: null,
                    totalPrice: null,
                }
            }
        },
        created(){
          eventBus.$on("AddedImg",(selectedImage) => {
            // this.$set(this.product, 'selectedImage', selectedImage);
            Object.assign(this.product, {'selectedImage': selectedImage});
            //this.product.selectedImage = selectedImage;
          })
        },
        methods: {
            addProduct(){
                console.log(this.product);
                this.product.totalPrice=this.product.count * this.product.price;
                eventBus.$emit("AddedProduct",this.product);
                this.product = {
                    title: null,
                    count: null,
                    price: null,
                    totalPrice: null
                },
                this.selectedImage= "";
            }

        }
    }

    
</script>

<style>
    
</style>
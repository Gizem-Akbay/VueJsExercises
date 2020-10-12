<template>
    <div class="card offset-2 col-md-3">
        <div class="card-body text-center d-flex align-items-center flex-column">
            <img height="128" class="img-responsive text-center mb-3"
                :src="product.selectedImage == null ? require('../assets/default.png') : product.selectedImage">
            <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
            <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">Choose Image</button>
        </div>
    </div>
</template>
<script>
    import {eventBus} from "../main";
    export default {
        data() {
            return {
                product: {
                    selectedImage: null
                } 
            }
        },
        methods:{
            onChange(e){
                const file = e.target.files[0];
                this.product.selectedImage=URL.createObjectURL(file);
                eventBus.$emit("AddedImg", this.product.selectedImage);
            }
    
        }
    }
        
</script>
<style></style>
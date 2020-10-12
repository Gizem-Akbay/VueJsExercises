<template>
    <div class="container">
        <h1 class="text-center">Adding Product Application</h1>
        <hr>
        <div class="row">
                <appAddImage></appAddImage>
                <appAddProduct></appAddProduct>
        </div>
        <br><br>
        <appProgressBar></appProgressBar>
        <br><br>
        <appProductsList></appProductsList>
    </div>
</template>

<script>
import AddImage from './components/AddImage.vue'
import AddProduct from './components/AddProduct.vue'
import ProductsList from './components/ProductsList.vue'
import ProgressBar from './components/ProgressBar.vue'


export default {
  name: 'App',
  components: {
    appAddImage : AddImage,
    appAddProduct : AddProduct,
    appProductsList : ProductsList,
    appProgressBar : ProgressBar,
  }
}
</script>

<style>
    body {
        background-color: aliceblue;
        padding-top: 20px;
        padding-bottom: 20px;
    }

    .card {
        margin-right: 5px;
        margin-bottom: 5px;
    }

    .card:last-child {
        margin-right: 0px;
    }

    .col-md-2 {
        max-width: 15.666667% !important;
    }

    .product-container {
        margin-left: 15px;
    }

</style>
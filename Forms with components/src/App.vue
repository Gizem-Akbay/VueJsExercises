<template>
    <div class="container">
        <h3>Working with Form Data</h3>
        <hr>
        <div class="row">
            <appForm></appForm>
            <appData></appData>
        </div>
    </div>
</template>
<script>
    import applicationForm from './components/applicationForm'
    import formData from './components/formData'
    export default {
      components: {
        appForm : applicationForm,
        appData:  formData 
      }
    }
</script>
<style>
</style>
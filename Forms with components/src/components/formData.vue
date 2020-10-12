<template>
    <div class="col-md-6">
        <div class="panel panel-info" v-if="Object.keys(this.dataList).length">
            <div class="panel-heading">
                <h4>Form Data</h4>
            </div>
            <div class="panel-body">
                <p>User Name: {{dataList.username}}</p>
                <p>Password: {{dataList.password}}</p>
                <p>Age: {{dataList.age}}</p>
                <p style="white-space: pre;">Message: {{dataList.message}} </p>
                <p><strong>Interests</strong></p>
                <ul>
                    <li v-for="item in dataList.interests" :key="item">{{item}}</li>
                </ul>
                <p>Gender:{{dataList.gender}}</p>
                <p>City: {{dataList.selectedCity}}</p>
            </div>
        </div>
    </div>
</template>
<script>
    import {eventBus} from "../main";
    export default{
        data() {
            return {
                dataList: {}
            }
        },
        created() {
            eventBus.$on("submittedData",(userData) => {
                this.dataList=userData;
            })
        }
    }
</script>
<style>
</style>
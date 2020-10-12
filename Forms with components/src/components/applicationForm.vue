<template>
    <div class="col-md-6">
        <div class="panel panel-warning">
            <div class="panel-heading">
                <h4>Application form</h4>
            </div>
            <div class="panel-body">
                <form>
                    <div class="row">
                        <div class="col-md-12">
                            <div class="form-group">
                                <label for="email">User Name</label>
                                <input type="text" id="username" class="form-control" v-model="userData.username">
                            </div>
                            <div class="form-group">
                                <label for="password">Passwoord</label>
                                <input type="password" id="password" class="form-control" v-model.lazy.trim="userData.password">
                            </div>
                            <div class="form-group">
                                <label for="age">Age</label>
                                <input type="number" id="age" class="form-control" v-model.number.trim="userData.age">
                            </div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12 form-group">
                            <label for="message">Message</label><br>
                            <textarea id="message" rows="3" class="form-control" v-model="userData.message"></textarea>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12">
                            <div class="form-group">
                                <label>
                                <input v-model="userData.interests" type="checkbox" value="Software"> Software
                                </label>
                                <label>
                                <input v-model="userData.interests" type="checkbox" value="Hardware"> Hardware
                                </label>
                            </div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12 form-group">
                            <label>
                            <input v-model="userData.gender" type="radio" value="Male"> Male
                            </label>
                            <label>
                            <input v-model="userData.gender" type="radio" value="Female"> Female
                            </label>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12 from-group">
                            <label>Şehir</label>
                            <select v-model="userData.selectedCity" class="form-control">
                                <option :selected="city == 'muğla'" v-for="city in userData.cities" :key="city">{{city}}</option>
                            </select>
                        </div>
                    </div>
                    <hr>
                    <div class="row">
                        <div class="col-md-12">
                            <button
                                @click.prevent="submit"
                                class="btn btn-primary">Send
                            </button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import {eventBus} from "../main";
    export default {
      data() {
        return {
          userData: {
            username: '',
            password: '',
            age: 30,
            message: '',
            interests: [],
            gender: '',
            cities : ["ankara","izmir","konya","muğla"],
            selectedCity: '',
          },
        }
      },
      methods: {
        submit(){
          eventBus.$emit("submittedData",this.userData);
        }
      }
    }
</script>

<style> 
</style>
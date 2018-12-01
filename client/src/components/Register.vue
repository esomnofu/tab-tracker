<template>
    <div>
        <form>
        <div class="container">  
            <div class="form-row">
                <div class="form-group col-md-6">
                <label for="email">Email</label>
                <input type="email" class="form-control" id="email" name="email" v-model="email" placeholder="email" required>
                </div>
                
                <div class="form-group col-md-6">
                <label for="password">Password</label>
                <input type="password" class="form-control" id="password" name="password" v-model="password" placeholder="Password" required>
                </div>
            </div>
            <button type="submit" class="btn btn-secondary btn-block" @click.prevent="onSignUp" v-show="email && password">Sign up for free!</button>  
            </div>
        </form>
    </div>
</template>

<script>

import AuthenticationService from '../services/AuthenticationService'

export default {
    data () {
        return {
            email : '',
            password : ''
        }
    },
    methods : {
       async onSignUp(){
            await AuthenticationService.register({
               email:this.email,
               password:this.password
           })
           .catch(
               (err) => console.log(err)
               
           )
        }
    }
}
</script>
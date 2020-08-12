<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col s12 m8 offset-m2">
                    <div class="login card-panel greys lighten-4 black-text center">
                        <h3>Register</h3>
                        <form>
                            <div class="input-field">
                                <i class="material-icons prefix">email</i>
                                <input type="text" v-model="email">
                                <label for="email">Email</label>
                            </div>
                            <div class="input-field">
                                <i class="material-icons prefix">lock</i>
                                <input type="password" v-model="password">
                                <label for="password">Password</label>
                            </div>
                            <button @click="register" class="btn btn-large grey lighten-4 black-text">Register</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import firebase from 'firebase'
export default {
    name: 'register',
    data: function() {
        return {
            email: '',
            password: '',
        }
    },
    methods: {
        register: function (e) {
            firebase.auth().createUserWithEmailAndPassword(this.email, this.password)
            .then(user => {
                let currentUser = firebase.auth().currentUser.email
                alert(`Account created for ${currentUser}`)
                this.$router.push('/')
            },
            err => {
                alert(err.message)
            })
            e.preventDefault();
        }
    }
}
</script>
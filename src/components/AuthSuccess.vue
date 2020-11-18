<template>
    <div>
        <h1>Success</h1>
        <button @click='logOut'>Logout</button>
        <img :src="photo">
        <p>{{name}}</p>
        <p>{{email}}</p>
        <p>{{userId}}</p>
        <p>{{user}}</p>
        
    </div>
</template>

<script>
import firebase from 'firebase'
export default {
    data(){
        return{
            name: '',
            userId: '',
            email: '',
            photo: '',
            user:{}
        }
    },
    created(){
        this.user = firebase.auth().currentUser;
        if(this.user){
            this.name = this.user.displayName;
            this.email = this.user.email;
            this.userId = this.user.uid;
            this.photo = this.user.photoURL;
        }
    },
    methods:{
        logOut(){
            firebase.auth().signOut();
        }
    }
}
</script>
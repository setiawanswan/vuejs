<template>
    <div>
        <div class="user_profile">
            <h3>User Information</h3>
            <ul>
                <li><span>Name : </span> {{ userName }} </li>
                <li><span>Last Name : </span> {{ userLastname }} </li>
                <li><span>Age : </span> {{ userAge }} </li>
            </ul>
            <h3>Parents</h3>
            <ul>
                <li><span>Mother : </span> {{ userParents.mother }} </li>
                <li><span>Father : </span> {{ userParents.father }} </li>
            </ul>
            <!-- Looping -->
            <h3>Parents</h3>
            <ul v-for="(key, value, index) in userParents" :key="index"> 
                <li>
                    <span> {{ key }} </span>
                    {{ value }}
                </li>
            </ul>
        </div>
        <button @click="updateName">Update Name</button>
        <button @click="updateLastname('Smith')">Update Last Name</button>
        <div>
            <input type="text" v-model="friendInput">
            <button @click="addFriend">Add friend</button>
        </div>
    </div>
</template>

<script>
import { bus } from '../../main.js'

    export default {
        data() {
            return {
                friendInput: ''
            }
        },
        props:{
            userName: String,
            userLastname: String,
            userAge: Number,
            userParents: Object,
            updateLastname: Function
        },
         methods:{
            updateName(){
                // this.userName = 'Francis Greg'
                this.$emit('updateName', 'Francis Greg')
            },
            addFriend(){
                bus.$emit('addFriend', this.friendInput)
            }
        }  
    }
</script>

<style>
    span {
        font-weight: 800;
    }
    .user_profile {
        border: 1px solid #2196F3;
        padding: 10px 20px;
    }
</style>
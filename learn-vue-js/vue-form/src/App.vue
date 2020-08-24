<template>
    <div>
        <form v-on:submit="submitForm">
            <div>
                <label for="username">id :</label>
                <input id="username" type="text" v-model="username">
            </div>
            <div>
                <label for="password">password :</label>
                <input id="password" type="password" v-model="password">
            </div>
            <button type="submit" >login</button>
        </form>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: "App",
        data: function(){
            return {
                username : '',
                password : '',
            }
        },
        methods :{
            submitForm: function(){
                event.preventDefault();
                console.log(this.username, this.password);

                let url = 'https://jsonplaceholder.typicode.com/users';
                let data = {
                    username: this.username,
                    password: this.password
                }
                axios.post(url , data)
                    .then(function(response){
                        console.log(response);
                    })
                    .catch(function(error){
                        console.log(error)
                    });

            }
        }


    }
</script>

<style scoped>

</style>
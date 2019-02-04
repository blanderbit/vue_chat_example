<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card card-default">
                    <div class="card-header">Example Component</div>

                    <div class="card-body" v-for="message in mess">
                        {{message}}
                    </div>
                    <button @click="send()">qwqwdqwd</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        data(){
            return{
                mess: []
            }
        },
        created() {
            window.Echo.private('everywhere.2')
                .listen('UserRegisteredEvent', (message) => {
                    console.log(message);
                    this.mess.push(message)
                });
        },
        methods:{
            send(){
                axios.post('/test-broadcast', {message: 'qweqweqwe'})
                    .then(e => console.log(e))
                    .then(e => console.log(e))
            },
        }
    }
</script>

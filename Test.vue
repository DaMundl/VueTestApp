<template> 
    <div class = "test">
    <h1> {{title}} </h1>
    <input type="text" v-model="title"></br>
    <p v-if= "showName" v-text= "user.first_name+ ' ' + user.last_name"> </p> 
    <p v-else= "showName">Nobody</p> 
    <ul>
    <li v-for= "item in items">{{item.title}}</li>
    </ul>  
    <button v-on:click= "greet('hello WOrld')"> Say Greeting</button> 
    <br />
    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
    <hr />
    <label>First Name: </label><input type="text" v-model="user.first_name">
    <br />
    <label>Last Name: </label><input type="text" v-model="user.last_name">
    <h3>{{fullName}}</h3>
    <h2>{{msg}}</h2>
    </div>
</template>


<script>
    export default {
        name: 'test',
        props:{
            msg: {
                type:String,
                default: "Foobar"
            }
        },
        data () {
            return {
                title: 'Hello World!',
                user: {
                    first_name: 'John',
                    last_name: 'Doe'
                },
                showName: true,
                items: [
                    {title: 'Item 1'},
                    {title: 'Item 2'},
                    {title: 'Item 3'}
                ]
            }
        },
        methods: {
            greet: function(greeting){
                alert(greeting);
            },
            pressKey: function(e){
                console.log(e.target.value);
            },
            enterHit: function(){
                console.log('You hit enter');
            }
        },
        computed: {
            fullName: function(){
                return this.user.first_name + ' ' + this.user.last_name;
            }
        }
    }


</script>

<style scoped>
</style>
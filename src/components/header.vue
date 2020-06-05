<template>
    <nav>
        <ul>
            <li><router-link to="/">Home</router-link></li>
            <li><router-link to="/history">History of Searches</router-link></li>
        </ul>

    </nav>
</template>

<script>
    import axios from 'axios';  export default {
        name: 'Users',
        data() {
            return {
                users: null,
            };
        },
        created: function() {
            axios
                .get('https://jsonplaceholder.typicode.com/users')
                .then(res => {
                    this.users = res.data;
                })
        }
    }
</script>

<style>

</style>
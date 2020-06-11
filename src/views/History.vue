<template>
    <div class="container">
        <h3 class="mt-3">Users:</h3>
        <table class="table">
            <thead>
            <tr>
                <th scope="col">Domain</th>
                <th scope="col">title</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="domain in history" :key="domain.id">
                <th scope="row">{{domain.domain}}</th>
                <td>{{domain.infoserver.title}}</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

    const BASE_URL = 'http://localhost:8083';
    import axios from 'axios';
    export default {
        name: 'History',
        data() {
            return {
                history: []
            };
        },
        created() {
            axios.get(BASE_URL + '/history')
                .then(response => {
                    console.log("[Success] History ")
                    console.log(response.data)
                    this.history = response.data.items
                    console.log(this.history)
                }).catch(err => {
                console.log("[Error] : Submit ", err)

            });
        },
        methods: {
            getlinkimg: function( value ){
                console.log("[FUNCTION GETLINKIMG ] : ", value)
                if (value == "")
                return {
                    link:"https://img.icons8.com/dotty/80/000000/id-not-verified.png"
                };
                else {
                    console.log("[Tiene algo ] : ", value)
                    return { link: ""+ String(value)};
                }
            }
        }
    }
    // <a href="https://icons8.com/icon/79675/identificación-no-verificada">Identificación no verificada icon by Icons8</a>
</script>

<style>

</style>
<template>
    <div class="container">
        <blockquote class="blockquote text-center">
            <p id="idtitle" class="font-weight-light">
                History of Searches
            </p>
        </blockquote>
        <table class="table">
            <tbody>
            <tr v-for="(domain, index) in history" :key="domain.id">
                <b-card no-body class="mb-1">
                    <b-card-header header-tag="header" class="p-1" role="tab">
                        <b-button block v-b-toggle="'accordion-'+index"  v-bind:variant="dark">{{domain.domain}}</b-button>
                    </b-card-header>
                    <b-collapse :id="'accordion-'+index" visible accordion="my-accordion" role="tabpanel">
                        <b-card-body>
                            <b-card-text><code> Servers Change: </code>{{ domain.infoserver.servers_changed }} <br>
                                <code> SSL Grade: </code>{{ domain.infoserver.ssl_grade }} <br>
                            <code> Previous SSL Grade: </code>{{ domain.infoserver.previous_ssl_grade }} <br>
                            <code> Title: </code>{{ domain.infoserver.title }}<br>
                            <code> Logo: </code>
                                <img v-bind:src="domain.infoserver.logo">
                                <br>
                            <code> Is Down: </code>{{ domain.infoserver.is_down }} </b-card-text>

                            <b-card
                                    title=""
                            >

                                    <code> Servers: </code>

                              <div v-for="server in history[index].infoserver.servers" v-bind:key="server.address">

                                    <b-card-text>
                                        <hr style="height:1px;border-width:0;color:ghostwhite;background-color:lightgrey">
                                        <code> Address: </code>{{ server.address }}<br>

                                    <code> SSL Grade: </code>{{ server.ssl_grade }}<br>

                                    <code> Country: </code>{{ server.country }}<br>

                                        <code> Owner: </code>{{ server.owner }}
                                    </b-card-text>
                            </div>
                            </b-card>

                        </b-card-body>
                    </b-collapse>
                </b-card>
                <div class="myDiv"></div>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

    const BASE_URL = 'http://localhost:8082';
    import axios from 'axios';
    export default {
        name: 'History',
        data() {
            return {
                history: [],
                link: ""
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
        }


    }
</script>

<style>
    .myDiv {
        padding-bottom: 5px;
    }
    img{
        width: 20px;

    }
    #idtitle{
        margin: 15px 0px;
        font-size: 120%;
    }
</style>
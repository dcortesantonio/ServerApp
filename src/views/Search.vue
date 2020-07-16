<template>
    <div class="container">
        <blockquote class="blockquote text-center">
            <p id="idtitle" class="font-weight-light">
                Search Domain
            </p>
        </blockquote>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
                    class="mt-3"
                    id="input-group-1"
                    label-for="input-1"
                    description="This it's the domain that you want to search."
            >
                <b-form-input
                        id="input-1"
                        v-model="form.domain"
                        type="domain"
                        placeholder="Enter domain"
                ></b-form-input>
            </b-form-group>

            <b-button class="px-5 ml-3 mr-8 "  type="submit" variant="outline-success"> Submit Search </b-button>
            <b-button class="px-md-5 ml-3 mr-8 " type="reset" variant="outline-secondary" > Reset Search </b-button>
        </b-form>
        <b-card class="mt-3" header="Form Data Result ">
            <section v-if="init">
                <pre class="m-0">Search a domain in the text box!</pre>
            </section>
            <section v-else>
                <section v-if="err">
                    <pre class="m-0">Error: {{ form }}</pre>
                </section>
                <section v-else>

                     <code> Servers Change: </code>{{ form.servers_changed }} <br>
                     <code> SSL Grade: </code>{{ form.ssl_grade }} <br>
                     <code> Previous SSL Grade: </code>{{ form.previous_ssl_grade }} <br>
                     <code> Logo: </code>   <img v-bind:src="form.logo"><br>
                    <code> Title: </code>{{ form.title }}<br>
                     <code> Is Down: </code>{{ form.is_down }}<br>
                    <hr style="height:1px;border-width:0;color:ghostwhite;background-color:lightgrey">

                    <code> Servers: </code>
                    <div v-for="server in form.servers" v-bind:key="server.address">
                          
                            <code> Address: </code>{{ server.address }}
                            <code> SSL Grade: </code>{{ server.ssl_grade }}
                            <code> Country: </code>{{ server.country }}
                            <code> Owner: </code>{{ server.owner }}
                         
                    </div>
                </section>
            </section>
        </b-card>
    </div>
</template>

<script>
    //Import axios to HTTP request
    const BASE_URL = 'http://localhost:8082';
    import axios from 'axios';
    export default {
        data() {
            return {
                form: {},
                show: true,
                err: false,
                init: true
            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault()
                console.log('DOMAIN: ', this.form.domain)
                axios.get(BASE_URL + '/search/'+ this.form.domain)
                    .then(response => {
                        console.log("[Success] Search:: ")
                        console.log(response.data)
                        this.form = response.data
                        this.err = false
                        this.init = false
                        this.$bvToast.toast('Search Successfully!', {
                            title: `[Succes] `,
                            variant: 'success',
                            solid: true
                        })
                    }).catch(err => {
                    this.form = "Domain not valid! \n Try again"
                    this.init = false

                    this.$bvToast.toast('Domain not valid', {

                        title: `[Error in Search] `,
                        variant: 'danger',
                        solid: true
                    })
                    this.err = true
                    console.log("[Error] : Submit Search ENDPOINT", err)
                });



            },
            onReset(evt) {
                evt.preventDefault()
                // Reset our form values
                this.form = {}
                // Trick to reset/clear native browser form validation state
                this.show = false
                this.init = true
                this.$nextTick(() => {
                    this.show = true
                })
            }
        }
    }
</script>
<style>
    #idtitle{
        margin: 15px 0px;
        font-size: 120%;
    }
    img{
        width: 20px;
    }
    #bl{
        height:1px;
        border-width:0;
        color:ghostwhite;
        background-color:ghostwhite;
    }
</style>
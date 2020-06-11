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
                        required
                        placeholder="Enter domain"
                ></b-form-input>
            </b-form-group>

            <b-button class="px-5 ml-3 mr-8 "  type="submit" variant="outline-success"> Submit Search </b-button>
            <b-button class="px-md-5 ml-3 mr-8 " type="reset" variant="outline-secondary" > Reset Search </b-button>
        </b-form>
        <b-card class="mt-3" header="Form Data Result ">
            <section v-if="errored">
                <pre class="m-0">We cannot load information.The domain it's not valid</pre>
            </section>
            <section v-else>
                <pre class="m-0">{{ form }}</pre>
            </section>
        </b-card>
    </div>
</template>

<script>
    //Import axios to HTTP request
    const BASE_URL = 'http://localhost:8083';
    import axios from 'axios';
    export default {
        data() {
            return {
                form: {},
                show: true,
                err: false
            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault()
                axios.get(BASE_URL + '/search/'+ this.form.domain)
                    .then(response => {
                        console.log("[Success] Search:: ")
                        console.log(response.data)
                        this.form = response.data
                        this.err = false
                        this.$bvToast.toast('Search Successfully!', {
                            title: `[Succes] `,
                            variant: 'success',
                            solid: true
                        })
                    }).catch(err => {

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
</style>
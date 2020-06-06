<template>
    <div class="container">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
                    class="mt-3"
                    id="input-group-1"
                    label="Email address:"
                    label-for="input-1"
                    description="We'll never share your email with anyone else."
            >
                <b-form-input
                        id="input-1"
                        v-model="form.domain"
                        type="domain"
                        required
                        placeholder="Enter domain"
                ></b-form-input>
            </b-form-group>

            <b-button class="px-5 ml-5 mr-14 "  type="submit" variant="outline-success"> Submit Search </b-button>
            <b-button class="px-md-5 ml-9 mr-8 " type="reset" variant="outline-secondary" > Reset Search </b-button>
        </b-form>
        <b-card class="mt-3" header="Form Data Result">
            <pre class="m-0">{{ form }}</pre>
        </b-card>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    domain: '',
                },
                show: true
            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault()
                alert(JSON.stringify(this.form))
            },
            onReset(evt) {
                evt.preventDefault()
                // Reset our form values
                this.form.domain = ''
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

</style>
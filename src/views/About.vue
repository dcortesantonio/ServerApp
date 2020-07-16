<template>
  <div role="tablist">
    <div>
      <b-col lg="4" class="plan" v-for="plan in plans" :key="plan.id">
        <b-button block v-bind:variant=" value ? 'primary' : 'secondary'" v-on:click="pickPlan(id)">
          <p class="price">€ {{plan.price}}</p>
          <p class="plan">{{plan.name}}</p>
        </b-button>
      </b-col>
    </div>
    <b-card no-body class="mb-1">
      <b-card-header header-tag="header" class="p-1" role="tab">
        <b-button block v-b-toggle.accordion-1  v-bind:variant="picked ? 'primary' : 'secondary'">Accordion 1</b-button>
      </b-card-header>
      <b-collapse id="accordion-1" visible accordion="my-accordion" role="tabpanel">
        <b-card-body>
          <b-card-text>I start opened because <code>visible</code> is <code>true</code></b-card-text>
          <b-card-text>Bodd</b-card-text>
        </b-card-body>
      </b-collapse>
    </b-card>

    <b-card no-body class="mb-1">
      <b-card-header header-tag="header" class="p-1" role="tab">
        <b-button block v-b-toggle.accordion-2  :variant="getColor(true)">Accordion 2</b-button>
      </b-card-header>
      <b-collapse id="accordion-2" accordion="my-accordion" role="tabpanel">
        <b-card-body>
          <b-card-text>Boddy</b-card-text>
        </b-card-body>
      </b-collapse>
    </b-card>

    <b-card no-body class="mb-1">
      <b-card-header header-tag="header" class="p-1" role="tab">
        <b-button block v-b-toggle.accordion-3 variant="info">Accordion 3</b-button>
      </b-card-header>
      <b-collapse id="accordion-3" accordion="my-accordion" role="tabpanel">
        <b-card-body>
          <b-card-text>Boddy2</b-card-text>
        </b-card-body>
      </b-collapse>
    </b-card>
  </div>
</template>

<script>

  const BASE_URL = 'http://localhost:8081';
  import axios from 'axios';
  export default {
    name: 'History',
    data() {
      return {
        history: []
        ,
        value: true
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
      getColor: function( value ){
        console.log("[FUNCTION GETLINKIMG ] : ", value)
        if (value == false)
          return { color:"secondary" };
        else {
          console.log("[Tiene algo ] : ")
          return { color:"outline-danger" };
        }
      }
    }
  }
  // <a href="https://icons8.com/icon/79675/identificación-no-verificada">Identificación no verificada icon by Icons8</a>
</script>

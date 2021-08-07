<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/Coronavirus.png')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Covid-19 Monitor
        </h1>

        <p class="subheading font-weight-regular">
          For help and collaboration,
          <br>please join our online
          <a
            href="https://www.github.com/daniel7byte"
            target="_blank"
          >Github Community</a>
        </p>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          Colombia
        </h2>

        <v-row justify="center">
          <p
            v-for="(element, i) in info.data.All" v-bind:key="i"
          >
            {{ i }}: {{ element }} <br/>
          </p>
        </v-row>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          Valle del Cauca
        </h2>

        <v-row justify="center">
          <p
            v-for="(element, i) in info.data['Valle del Cauca']" v-bind:key="i"
          >
            {{ i }}: {{ element }} <br/>
          </p>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'HelloWorld',

    data () {
      return {
        info: null
      }
    },

    async mounted () {
      await axios
        .get('https://covid-api.mmediagroup.fr/v1/cases?country=Colombia')
        .then(response => {
            this.info = response
            console.log(JSON.stringify(response.data))
          }
        )
    }
  }
</script>

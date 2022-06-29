<template>
  <div class="wrapper">
    <div class="container">
      <Title />
      <Form @submit-form="getWeather" />
      <Results :results="results" />
      <Loading v-if="loading.value" />
    </div>
  </div>

</template>
<script setup>

import Title from "./components/Title.vue"
import Results from "./components/Results.vue"
import Form from "./components/Form.vue"
import axios from "axios"
import { reactive, ref } from "vue"
import "./assets/base.css"
import Loading from "./components/Loading.vue"
const results = reactive({
  country: "",
  cityName: "",
  temperature: "",
  conditionText: "",
  icon: ""
})
const loading = ref(false)

const getWeather = (city) => {
  loading.value = true;
 
  axios.get(`https://api.weatherapi.com/v1/current.json?key=bf295d63eb764d2caa764008222606&q=${city}&aqi=no`)
    .then(res => {
      results.country = res.data.location.country,
        results.cityName = res.data.location.name,
        results.temperature = res.data.current.temp_c,
        results.conditionText = res.data.current.condition.text,
        results.icon = res.data.current.condition.icon

    }).catch(err=>{
      alert("error detected. Please reload the page.")
    })
    loading.value = false;
   
}

</script>


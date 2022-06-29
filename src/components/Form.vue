<template>
    <form @submit.prevent="submitForm">
        <input type="text" placeholder="type city here" v-model="city">
        <button type="submit">Get Weather!</button>
    </form>
</template>
<script setup>
import {ref} from "vue"
const city = ref("")
const submitForm = () =>{
  emits("submit-form",city.value)
}
const emits = defineEmits([
  "submit-form"
])
</script>
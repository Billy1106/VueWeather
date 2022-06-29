<template>
    <div v-if="props.results.country">{{props.results.country}}</div>
    <div v-if="props.results.country">{{props.results.cityName}}</div>
    <div v-if="props.results.country">{{props.results.temperature}}</div>
    <div v-if="props.results.country"><img :src="props.results.icon" alt="icon" /></div>
    <span v-if="props.results.country">{{props.results.conditionText}}</span>
</template>
<script setup>
const props = defineProps({
    results:Object
})
</script>

<style>
</style>
<script setup>
import { onBeforeUnmount, onMounted, shallowRef } from 'vue'
import TabComponent from './components/TabComponent.vue'
import TabPanel from './components/TabPanel.vue'

let activeTab = shallowRef('details')
let certificatesNum = shallowRef(10)
let agreementsNum = shallowRef(99)
let interval = shallowRef(null)

onMounted(() => {
	interval.value = setInterval(() => {
		certificatesNum.value = Math.floor(Math.random() * 100)
		agreementsNum.value = Math.floor(Math.random() * 100)
	}, 2000)
})

onBeforeUnmount(() => {
	clearInterval(interval.value)
})
</script>

<template>
	<head>
		<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons"></link>
	</head>
	<h1>Let's build some tabs!</h1>
	<!-- These are external buttons, to test the functionality of your component(s) -->
	<!--Please don't remove these-->
	<div class="buttons">
		<button @click="activeTab = 'details'">Details</button>
		<button @click="activeTab = 'assortment'">Assortment</button>
		<button @click="activeTab = 'questionnaires'">Questionnaires</button>
		<button @click="activeTab = 'certificates'">Certificates</button>
		<button @click="activeTab = 'agreements'">Agreements</button>
	</div>

	<!-- Put the tabs component(s) here, with a v-model set to `activeTab` -->

	<TabComponent v-model="activeTab">
		<TabPanel id="details" label="Details" imageText="dashboard">Details Content is awesome</TabPanel>
		<TabPanel id="assortment" label="Assortment" suffix="suffix">Assortment Content is awesome</TabPanel>
		<TabPanel id="questionnaires" label="Questionnaires" suffix="123">Questionnaires Content is awesome</TabPanel>
		<TabPanel id="certificates" label="Certificates">Certificates Content is awesome</TabPanel>
		<TabPanel id="agreements" label="Agreements" disabled="true">Agreements Content is awesome</TabPanel>
	</TabComponent>

</template>


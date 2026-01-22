<script setup>
import { onBeforeUnmount, onMounted, shallowRef } from 'vue'
import TabComponent from './components/TabComponent.vue'

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
		<button 
			@click="activeTab = 'details'" 
			:class="{selected: activeTab === 'details'}" 
			label="details">
				<span role="img" class="material-icons">dashboard</span>
			Details
			<span class="button-append">10</span>
		</button>
		<button @click="activeTab = 'assortment'" :class="{selected: activeTab === 'assortment'}" label="assortment">Assortment</button>
		<button @click="activeTab = 'questionnaires'" :class="{selected: activeTab === 'questionnaires'}" label="questionnaires"><span role="img" class="material-icons">assignment_return</span>Questionnaires</button>
		<button @click="activeTab = 'certificates'" :class="{selected: activeTab === 'certificates'}" label=""certificates>Certificates<span class="button-append"> 29</span></button>
		<button @click="activeTab = 'agreements'" :class="{selected: activeTab === 'agreements'}" label="label">Agreements</button>
	</div>

	<!-- Put the tabs component(s) here, with a v-model set to `activeTab` -->

	<TabComponent v-model="activeTab"></TabComponent>

</template>


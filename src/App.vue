<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png">
		<Template msg="test chartjs" />
	</div>
</template>

<script>
	import Template from './components/Template.vue'

	export default {
		name: 'app',
		components: {
			Template
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>

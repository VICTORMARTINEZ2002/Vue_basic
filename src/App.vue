<template>
	<div class="app-container">
		<myHeader />
		<MyLateralMenu />
		<div class="atividade-container">
			<MyAtividade />
		</div>
	</div>
</template>

<script>
import MyAtividade from './components/myAtividade.vue';
import myHeader from './components/myHeader';
import MyLateralMenu from './components/myLateralMenu.vue';

export default {
	name: 'App',
	components: {
		myHeader,
		MyLateralMenu,
		MyAtividade
	}
}
</script>

<style scoped>
.app-container {
	position: relative;
	height: 100dvh;
	overflow: scroll;
}

.atividade-container {
	position: absolute;
	top: 60px;
	left: 300px;
	right: 0;
	bottom: 0;
	padding: 1rem;
	overflow-y: auto;
	box-sizing: border-box;
	background-color: #ffffff;
}
</style>

<style>
html, body {
	margin: 0;
	padding: 0;
	width: 100%;
	height: 100%;
	overflow: clip;
	min-width: 800px;
}
</style>

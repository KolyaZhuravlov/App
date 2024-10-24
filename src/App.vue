<template>
	<div class="container">
	  <h1>План по навчанню Vue.js</h1>
	  <p v-if="currentParagraph">{{ currentParagraph }}</p>
	  <ul class="horizont-list">
		 <li v-for="(block, index) in blocks" :key="index">
			<button @click="newParagraf(index)" :class="{ active: currentIndex === index }">
			  {{ block }}
			</button>
		 </li>
	  </ul>
	  <br />
	  <ul class="back-upp">
		 <li><button @click="goBack" :disabled="currentIndex === 0">{{ back }}</button></li>
		 <li><button @click="goForward" :disabled="currentIndex === blocks.length - 1">{{ upp }}</button></li>
	  </ul>
	</div>
 </template>
 
 <script>
 export default {
	data() {
	  return {
		 currentParagraph: '', 
		 blocks: [
			'Коля',
			'Вася',
			'Петя',
			'Саша',
			'Миша'
		 ],
		 par: [
			'Это параграф для Коли.',
			'Это параграф для Васи.',
			'Это параграф для Пети.',
			'Это параграф для Саши.',
			'Это параграф для Миши.'
		 ],
		 currentIndex: -1, 
		 back: 'Назад',
		 upp: 'Вперед'
	  };
	},
	methods: {
	  newParagraf(index) {
		 this.currentIndex = index; 
		 this.currentParagraph = this.par[index];
	  },
	  goBack() {
		 if (this.currentIndex > 0) {
			this.currentIndex--; 
			this.currentParagraph = this.par[this.currentIndex]; 
		 }
	  },
	  goForward() {
		 if (this.currentIndex < this.blocks.length - 1) {
			this.currentIndex++; 
			this.currentParagraph = this.par[this.currentIndex]; 
		 }
	  }
	}
 }
 </script>
 
 <style scoped>
 .container {
	transition: background-color 0.3s;
	background: white;
	width: 600px;
	border: 2px solid #ccc;
	height: 300px;
	position: absolute;
	left: 0;
	right: 0;
	margin: 0 auto;
	top: 100px;
	border-radius: 20px;
 }
 .container:hover {
	transform: scale(1.01);
 }
 p {
	font-size: 22px;
 }
 .horizont-list {
	list-style-type: none; 
	padding: 0; 
	margin: 0; 
 }
 .horizont-list li {
	display: inline;
	margin-right: 10px;
 }
 .horizont-list button {
	padding: 10px; 
	background-color: green; 
	color: white; 
	border: none; 
	border-radius: 5px; 
	cursor: pointer; 
	transition: background-color 0.3s;
 }
 .horizont-list button.active {
	background-color: rgb(0, 94, 255); 
 }
 .back-upp button {
	background-color: blue;
	border-radius: 5px;
	color: white; 
 }
 </style>
 
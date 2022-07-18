<template>
	<div class="game">
		<h1 class="title">Reaction Game</h1>
		<span class="span">with vuejs</span>
		<button :disabled="options.clicked" @click="startGame" class="btn">Click</button>
		<Block @end="endGame" :delay="options.delay" v-if="options.clicked"/>
		<Results :score="options.score" v-if="options.showResults"/>
	</div>
</template>

<script setup>
import Block from "./Block.vue"
import Results from "./Results.vue"
import {reactive} from "vue";


const options = reactive({
	clicked: false,
	delay: null,
	score: null,
	showResults: false
})

const startGame = () => {
	options.clicked = true
	options.delay = 150 + Math.floor(Math.random() * 5000);
	options.showResults = false;
}

const endGame = (reactionTimer) => {
	options.clicked = false;
	options.score = reactionTimer;
	options.showResults = true;
}

</script>

<style scoped>

.title {
	margin-bottom: 5px;
	color: #42b883;
	font-weight: 800;
}
.span {
	font-family: sans-serif;
	font-size: 12px;
	text-transform: uppercase;
	opacity: 0.5;
	font-weight: 600;
}
.game {
	display: flex;
	flex-direction: column;
	align-items: center;
}
.btn {
	margin-top: 10px;
	background: #42b883;
	border: none;
	color: #fff;
	border-radius: 2px;
	cursor: pointer;
	padding: 10px 25px;
	transition: all 0.3 ease-in;
}
.btn:disabled {
	background: #ccc;
	color: #333;
	cursor: not-allowed;
	opacity: 0.5;
	transition: all 0.3 ease-in;
}

</style>

<script setup>
import {onMounted, reactive, watch,} from "vue";


const options = reactive({
	showBlock: false,
	timer: null,
	reactionTimer: 0,
})

const props = defineProps({
	delay: Number
})

const emit = defineEmits(['end']);

const startTimer = () => {
	options.timer = setInterval(() => {
		options.reactionTimer += 10;
	}, 1)
}

const stopTimer = () => {
	options.showBlock = false;
	clearInterval(options.timer);
	emit('end', options.reactionTimer)
}

onMounted(() => {
	setTimeout(() => {
		options.showBlock = true
		startTimer();
	}, props.delay)
})

</script>

<template>
	<div @click="stopTimer" class="block" v-if="options.showBlock">HURRY UP!</div>
</template>

<style scoped>
.block {
	width: 70%;
	height: 300px;
	background: #42b883;
	border-radius: 10px;
	display: flex;
	justify-content: center;
	align-items: center;
	color: #fff;
	margin-top: 20px;
	cursor: pointer;
}

</style>

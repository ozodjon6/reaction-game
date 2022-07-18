<script setup>
import {onMounted, reactive, ref, watch} from "vue";

const props = defineProps({
	score: Number
})

const rank = ref("");


onMounted(() => {
	if (props.score < 250) {
		rank.value = "Voy-buy! Ajoyib barmoqlar";
	} else if (props.score < 300) {
		rank.value = "Ajoyib reaktsiya!";
	} else if (props.score < 400) {
		rank.value = "Zaif reaktsiya.";
	} else {
		rank.value = "Qani qara mana, yana tushib ketyabsan!";
	}
})

</script>

<template>
	<p class="result">
		Your reaction time is: <span>{{ score }}</span> ms
	</p>
	<p class="message">{{ rank }}</p>
</template>

<style scoped>
.result {
	margin: 8px;
	font-size: 13px;
	color: rgba(51, 51, 51, 0.616);
}
.result span {
	font-weight: 700;
}
.message {
	font-size: 20px;
	font-weight: 700;
}

</style>

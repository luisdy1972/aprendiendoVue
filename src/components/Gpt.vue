<script setup>
import axios from "axios"
import { ref } from "vue"
// const axios = require("axios")
const API_KEY = "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"
const prompt = "Muestrame un hola mundo en JS"

let response = ref()
axios
	.post(
		"https://api.openai.com/v1/engines/davinci-codex/completions",
		{
			prompt: prompt,
			max_tokens: 20,
			n: 1,
			stop: "\n",
		},
		{
			headers: {
				"Content-Type": "application/json",
				Authorization: `Bearer ${API_KEY}`,
			},
		}
	)
	.then((response) => {
		console.log(response)
		const completions = response.data.choices[0].text
		console.log(completions)
		response.value = completions
	})
	.catch((error) => {
		if (error) {
			console.error(error)
			response.value = error
		}
	})
</script>
<template>
	<div>
		<h1>Gpt</h1>
		<p>{{ response }}</p>
	</div>
</template>
<style></style>

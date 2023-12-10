<template>
	<FormKitSchema :schema="schema" />
</template>

<script setup>
import { FormKitSchema } from "@formkit/vue";
import { ref } from "vue";
const schema = ref([
	{
		$el: "h1",
		children: "Login",
	},
	{
		$formkit: "form",
		children: [
			{
				$formkit: "email",
				name: "email",
				label: "Email",
				validation: "required|email",
			},
			{
				$formkit: "password",
				name: "password",
				label: "Password",
				validation: "required|length:5,16",
			},
		],
	},
]);
</script>

<style lang="scss" scoped></style>

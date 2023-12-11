<template>
	<FormKitSchema :schema="divSchema" />
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
const divSchema = ref([
 {
  $el: 'div',
  children: [
   {
    $el: 'h1',
    children: 'This is a heading',
   },
   {
    $el: 'p',
    children: 'This is a paragraph',
   },
   {
    $el: 'p',
    children: 'This is another paragraph but with styling',
    attrs: {
     style: {color: 'blue'}
    }
   }
  ]
 }
])
</script>

<style lang="scss" scoped></style>

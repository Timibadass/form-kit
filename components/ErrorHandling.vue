<template>
	<FormKit
		type="form"
		submit-label="Submit"
		@submit="createUser"
	>
		<FormKit
			name="fullName"
			id="fullName"
			type="text"
			label="Full Name"
			validation="required"
		/>
		<FormKit
			name="email"
			id="email"
			type="email"
			label="Email"
			validation="required"
		/>
		<FormKit
			name="address"
			id="address"
			label="Address"
			type="textarea"
			validation="required"
		/>
	</FormKit>
</template>

<script setup>
import { ref } from "vue";
const errors = ref([""]);

const createUser = (v, node) => {
	if (v.email.includes("yopmail")) {
		node.setErrors(["Something happened"], {
			email: "Please enter a valid email",
		});
	}
	// setTimeout(() => {
	//  errors.value = ['Something happened']
	// }, 2000);
};
</script>

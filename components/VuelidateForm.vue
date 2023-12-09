<template>
	<div>
		<form @submit.prevent="validateForm">
			<label for="car">Car brand</label>
			<select name="car" id="car" v-model="state.car">
				<option :value="car" v-for="car in cars" :key="car">{{ car }}</option>
			</select>
			<p v-for="error of v$?.car?.$errors" :key="error.$uid" class="error">
				{{ error.$message }}
			</p>

			<label for="seats">Number of seats</label>
			<select name="seats" id="seats" v-model="state.numberOfSeats">
				<option :value="seat" v-for="seat in seats" :key="seat">
					{{ seat }}
				</option>
			</select>
			<p v-for="error of v$?.numberOfSeats?.$errors" :key="error.$uid" class="error">
    {{ error.$message }}
			</p>
			<label for="price">Price</label>
			<input type="number" name="price" id="price" v-model="state.price" />
			<p v-for="error of v$?.price?.$errors" :key="error.$uid" class="error">
				{{ error.$message }}
			</p>
			<button>Submit</button>
		</form>
	</div>
</template>

<script setup>
import { useVuelidate } from "@vuelidate/core";
import { maxValue, minValue, required } from "@vuelidate/validators";
import { reactive } from "vue";

const cars = ref(["Toyota", "Lexus", "Honda", "Ford", "Chevrolet"]);
const seats = ref(8);
const state = reactive({
	numberOfSeats: "",
	car: "",
	price: "",
});

const rules = {
	car: { required },
	numberOfSeats: { required },
	price: {
		required,
		minValue: minValue(10000),
		maxValue: maxValue(50000),
	},
};

const v$ = useVuelidate(rules, state);

const validateForm = async () => {
	const isValid = await v$.value.$validate();
	if (isValid) {
		// do something
	}
};
</script>
<style>
.error {
	color: red;
}
</style>

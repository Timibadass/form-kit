<template>
 <div>
  <FormKit type="form" submit-label="Submit" @submit="validateForm" use-local-storage>
   <FormKit label="Car brand" type="select" :options="cars" name="cars" v-model="state.car" validation="required" />
   <FormKit label="Number of seats" type="select" :options="seats" name="numberOfSeats" v-model="state.numberOfSeats" validation="required" />
   <FormKit label="Price" type="number" v-model="state.price" name="price" validation="required | min:10000 | max:50000" :validation-messages="{
    max: ({ node: { value } }) => `${value} is above the allowed price range`
   }" />
  </FormKit>
 </div>
</template>

<script setup>
import { reactive } from "vue";

const cars = ref(["Toyota", "Lexus", "Honda", "Ford", "Chevrolet"]);
const seats = ref([1,2,3,4]);
const state = reactive({
	numberOfSeats: "",
	car: "",
	price: "",
});

const validateForm = async () => {
	console.log(state.value);
};
</script>

<style lang="scss" scoped>

</style>
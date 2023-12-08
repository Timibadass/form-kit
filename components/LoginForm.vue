<template>
	<div>
		<FormKit type="form" submit-label="Login" @submit="logDetails">
			<FormKit type="email" name="email" label="Email" validation="required" />
			<FormKit type="password" name="password" label="Password" validation="required" />
		</FormKit>
	</div>
</template>

<script>
const logDetails = (v) => {
  console.log(v);
}
</script>

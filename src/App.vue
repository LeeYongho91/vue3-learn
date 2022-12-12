<template>
	<div>
		<LabelInput v-model="title" />
		<UserName v-model:firstname="firstname" v-model:lastname="lastname" />
		<LabelInput
			:modelValue="username"
			@update:modelValue="newValue => (username = newValue)"
		/>
		<button @click="test">클릭</button>
	</div>
</template>

<script>
import { ref } from 'vue';
import LabelInput from '@/components/LabelInput.vue';
import UserName from '@/components/UserName.vue';
export default {
	components: {
		LabelInput,
		UserName,
	},
	setup() {
		const title = ref('');
		const firstname = ref('');
		const lastname = ref('');
		const test = () => {
			console.log(title.value);
			console.log(firstname.value);
			console.log(lastname.value);
			console.log(`test`);
		};
		return { title, firstname, lastname, test };
	},
};
</script>

<style lang="scss" scoped></style>

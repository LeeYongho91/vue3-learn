<template>
	<div>
		{{ msg }}
		{{ message }}
		<input type="text" v-model="message" />
		<button @click="sayHello">click</button>
		<PostItem type="news" title="제목" contents="내용" :is-like="true" />
		<PostItem type="news" title="제목" contents="내용" :is-like="true" />
		<PostItem type="news" title="제목" contents="내용" :is-like="true" />
		<hr />
		<MyButton class="parent-class"></MyButton>
	</div>
</template>

<script setup>
import { ref } from 'vue';
import PostItem from '@/components/setup/PostItem.vue';
import MyButton from '@/components/setup/MyButton.vue';
import axios from 'axios';

const msg = 'hello World';
const message = ref('');
const sayHello = () => {
	alert('hello world');
};
const response = await axios(
	'	https://dummy.restapiexample.com/api/v1/employees',
);
console.log('response', response);
</script>

<style lang="scss" scoped></style>

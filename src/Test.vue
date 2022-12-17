<template>
	<div class="container py-4">
		<input type="text" ref="inputRef" />
		<p v-if="inputRef">{{ inputRef.value }}</p>
		<p v-if="inputRef">{{ $refs.inputRef }}</p>
		<hr />
		<ul>
			<li
				v-for="fruit in fruits"
				:key="fruit"
				:ref="el => itemRefs.push(el.textContent)"
			>
				{{ fruit }}
			</li>
		</ul>
		<TemplateRefsChild ref="child" />
	</div>
</template>

<script>
import { onMounted, ref } from 'vue';
import TemplateRefsChild from '@/components/TemplateRefsChild.vue';

export default {
	name: 'test-component',
	components: {
		TemplateRefsChild,
	},
	setup() {
		const inputRef = ref(null);
		console.log('setup:', inputRef.value);

		onMounted(() => {
			inputRef.value.value = 'hello';
			console.log('onMounted:', inputRef.value);
			itemRefs.value.forEach(item => console.log(item));
			console.log('child-message', child.value.message);
		});

		const fruits = ref(['사과', '딸기', '포도']);
		const itemRefs = ref([]);
		const child = ref(null);

		return { inputRef, fruits, itemRefs, child };
	},
};
</script>

<style lang="scss" scoped></style>

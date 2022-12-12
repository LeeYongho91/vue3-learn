<template>
	<div>
		<FancyButton></FancyButton>
		<AppCard>
			<template #default="{ childMessage, helloMessage }"
				>제목입니다. {{ childMessage }}{{ helloMessage }}</template
			>
			<!-- <template v-slot:default>내용입니다.</template>
			<template v-slot:footer>푸터입니다.</template> -->
		</AppCard>
		<AppCard>
			<template #[slotArgs]>헤더입니다.</template>
			<template #default>안녕하세요</template>
			<template #footer="{ footerMessage }">ㅇㅇ {{ footerMessage }}</template>
		</AppCard>
	</div>
</template>

<script>
import FancyButton from '@/components/FancyButton.vue';
import AppCard from '@/components/AppCard.vue';
import { ref } from 'vue';

export default {
	components: {
		FancyButton,
		AppCard,
	},

	setup() {
		const sayHello = () => {
			alert('안녕하세요');
		};

		const slotArgs = ref('header');

		return { sayHello, slotArgs };
	},
};
</script>

<style lang="scss" scoped></style>

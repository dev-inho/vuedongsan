<template>
	<!-- 디테일 박스 -->
	<div class="black-bg"
        v-if="isModal">
		<div class="white-bg">
			<img :src="img" style="width: 100%">
			<h4>{{title}}</h4>
			<p>{{content}}</p>
			<p>{{price}}원</p>
			<button data-val="close">닫기</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "Modal",
	props: {
		title: String,
		content: String,
		price: Number,
		isModal: Boolean,
		img: Image,
	},
	methods: {
	}
}
</script>

<style scoped>

</style>
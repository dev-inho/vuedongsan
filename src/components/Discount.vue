<template>
	<!-- 할인 문구 -->
	<div class="discount">
		<h4>지금 결제하면 {{percent}}% 할인</h4>
	</div>
</template>

<script>
export default {
	name: "Discount",
	props: {
		percent: Number
	}
}
</script>

<style scoped>
.discount {
	background: #eee;
	padding: 10px;
	margin: 10px;
	border-radius: 5px;
}
</style>
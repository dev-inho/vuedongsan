<template>
	<!-- 상품 목록-->
	<div>
		<img alt="방 그림" class="room-img"
            :src="product.image">
		<h4
			@click="$emit('modalFunc', 'open', product.id)">{{product.title}}</h4>
		<p>{{product.price}} 만원</p>
		<button
			@click="$emit('report', i)">허위매물 신고</button>
		<span>신고 수 : {{product.count}}</span>
	</div>
</template>

<script>
export default {
	name: "Card",
	props: {
		product: Object,
		i: Number,
	},
}
</script>

<style scoped>

</style>
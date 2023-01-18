<template>
	<!-- 디테일 박스 -->
	<div class="black-bg"
        v-if="isModal">
		<div class="white-bg">
			<img :src="img" style="width: 100%">
			<h4>{{title}}</h4>
			<p>{{content}}</p>
			<input type="text"
				v-model="quantity"/>
			<p>{{quantity}}개월 선택함 : {{price * quantity}}원</p>
			<button @click="closeModal" data-val="close">닫기</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "Modal",
	data() {
		return {
			quantity: 1,
		}
	},
	watch: {
		quantity(v, ov) { // 수량 유효성 검사
			if (isNaN(v)) {
				this.quantity = 1;
				return alert("수량은 숫자만 입력이 가능합니다.");
			}
			if (v > 12) {
				this.quantity = ov;
				return alert("수량은 최대 12까지 가능합니다.");
			}
		}
	},
	beforeUpdate() {
		if (this.quantity === 2) {
			alert('2개월은 너무 적음.. 안팝니다')
		}
	}
	props: {
		title: String,
		content: String,
		price: Number,
		isModal: Boolean,
		img: Image,
	},
	methods: {
		closeModal(e) {
			const target = e.target;
			const dataVal = target.getAttribute("data-val");

			this.$emit("modalFunc", dataVal);
		}
	}
}
</script>

<style scoped>

</style>
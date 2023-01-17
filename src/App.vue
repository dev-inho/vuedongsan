<template>
	<Modal @click="modalFunc"
		:title="title" :content="content" :price="price" :isModal="isModal" :img="img"></Modal>

	<!-- Nav Bar-->
	<div class="menu">
		<a
			v-for="(navEl, i) in navList" :key="i">
			{{navEl}}
		</a>
	</div>

	<Discount></Discount>
	<Card
		@modalFunc="modalFunc" @report="report"
		v-for="(product, i) in oneroom" :key="i"
		:product="product" :i="i"></Card>
</template>

<script>
import oneroom from "./assets/oneroom";
import Discount from "@/components/Discount.vue";
import Modal from "@/components/Modal.vue";
import Card from "@/components/Card.vue";

export default {
    name: 'App',
	methods: {
		report(dataIndex) { // 신고 수
			this.products[dataIndex].count++;s
		},
		modalFunc(dataVal, dataId) {
			if (dataVal === "open") {
				this.title = this.oneroom[dataId].title;
				this.content = this.oneroom[dataId].content;
				this.price = this.oneroom[dataId].price;
				this.img = this.oneroom[dataId].image;
				this.isModal = true;
			}
			else {
				this.isModal = false;
			}
		}
	},
	data() {
		return {
			products: [{
				img: require("./assets/room0.jpg"),
				name:'역삼동원룸',
				price: 60,
				count: 0,
			}, {
				img: require("./assets/room1.jpg"),
				name: '천호도 원룸',
				price: '가격은 아무거나',
				count: 0,
			}, {
				img: require("./assets/room2.jpg"),
				name: '마포구 원룸',
				price: '가격은 아무거나',
				count: 0,
			}],
			navList: ['Home', 'Shop', 'About'],
			isModal: false,
			oneroom: oneroom,
			title: "",
			content: "",
			price: 0,
			img: ""
		}
	},
    components: {
        Card,
        Modal,
        Discount
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
	background: darkslateblue;
	padding: 15px;
	border-radius: 5px;
}
.menu a {
	color: white;
	padding: 10px;
}
.room-img {
	width: 100%;
	margin-top: 40px;
}
body {
	margin: 0;
}
div {
	box-sizing: border-box;
}
.black-bg {
	width: 100%;
	height: 100%;
	background: rgba(0,0,0,0.5);
	position: fixed;
	padding: 20px;
}
.white-bg {
	width: 100%;
	background: white;
	border-radius: 8px;
	padding: 20px;
}
.button-box {
	display: flex;
	justify-content: center;
}
</style>

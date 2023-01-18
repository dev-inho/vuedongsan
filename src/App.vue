<template>
	<Transition name="fade">
		<Modal @modalFunc="modalFunc"
            :title="title" :content="content" :price="price" :isModal="isModal" :img="img"></Modal>
	</Transition>

	<!-- Nav Bar-->
	<div class="menu">
		<a
			v-for="(navEl, i) in navList" :key="i">
			{{navEl}}
		</a>
	</div>

	<Discount
		v-if="showDiscount" :percent="percent"></Discount>

	<button @click="sortProduct">가격낮은정렬</button>
	<button>되돌리기</button>

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
	computed: {
	},
	methods: {
		sortProduct() {
			this.oneroom.sort((a, b) => {
				return a.price - b.price;
			});
		},
		report(dataIndex) { // 신고 수
			this.oneroom[dataIndex].count++;
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
	mounted() {
		setInterval(() => {
			if (this.percent > 0) {
				this.percent -= 1;
			}
		}, 1000);
	},
	data() {
		return {
			percent: 30,
			showDiscount: true,
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

/* animation */
.start {
	opacity: 0; /* 투명도 */
	transition: all 1s; /* 지연 */
}
.end {
	opacity: 1;
}
.fade-enter-from {
	opacity: 0;
}
.fade-enter-active {
	transition: all 1s;
}
.fade-enter-to {
	opacity: 1;
}
.fade-leave-from {
	opacity: 0;
}
.fade-leave-active {
	transition: all 1s;
}
.fade-leave-to {
	opacity: 1;
}
</style>

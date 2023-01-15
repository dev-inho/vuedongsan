<template>
	<div class="menu">
		<a
			v-for="(navEl, i) in navList" :key="i">
			{{navEl}}
		</a>
	</div>
	<div v-for="(product, i) in products" :key="product">
		<h4>{{product.name}}</h4>
		<p>{{product.price}} 만원</p>
		<button
			@click="report" :data-index="i">허위매물 신고</button>
		<span>신고 수 : {{product.count}}</span>
	</div>
</template>

<script>
export default {
    name: 'App',
	methods: {
		report(e) { // 신고 수
			const target = e.target;
			const dataIndex = target.getAttribute("data-index");

			this.products[dataIndex].count++;
		}
	},
	data() {
		return {
			products: [{
				name:'역삼동원룸',
				price: 60,
				count: 0,
			}, {
				name: '천호도 원룸',
				price: '가격은 아무거나',
				count: 0,
			}, {
				name: '마포구 원룸',
				price: '가격은 아무거나',
				count: 0,
			}],
			navList: ['Home', 'Shop', 'About']
		}
	},
    components: {
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
</style>

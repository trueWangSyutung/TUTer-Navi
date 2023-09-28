<template>
	<view id="app">
		<view class="font">
			<image mode="aspectFit" class="img" src="../../static/biglogo.png" />
			天理导航 · TUTer-Navi
		</view>
		<view class="search">
			<input @input="onInput" class="input" type="text" placeholder="请输入要搜索的内容" />
			<view class="uni-list">
				<button data-mode="gg" class="com"  style=" display: flex;flex-direction: row; align-items: center; justify-content: space-between; box-sizing: border-box;"  @click="onGoogle">
					<image src="../../static/logos/google.png" style=" height: 50px;" mode="aspectFit"></image>
				</button>
				<button data-mode="bd" class="com"  style=" display: flex;flex-direction: row; align-items: center; justify-content: space-between; box-sizing: border-box;"  @click="onGoogle">
					<image src="../../static/logos/baidu.png" style=" height: 50px;" mode="aspectFit"></image>
				</button>
				<button data-mode="bing" class="com"  style="display: flex;flex-direction: row; align-items: center; justify-content: space-between; box-sizing: border-box;"  @click="onGoogle">
					<image src="../../static/logos/bing.jpg" style=" height: 50px;" mode="aspectFit"></image>
				</button>
				<button data-mode="ggxs" class="com"  style="; display: flex;flex-direction: row; align-items: center; justify-content: space-between; box-sizing: border-box;"  @click="onGoogle">
					<image src="../../static/logos/xueshu.png" style=" height: 50px;" mode="aspectFit"></image>
				</button>
				<button data-mode="zhwiki" class="com" style=" display: flex;flex-direction: row; align-items: center; justify-content: space-between; box-sizing: border-box;"  @click="onGoogle">
					<image src="../../static/logos/wikipedia.png" style=" height: 50px;" mode="aspectFit"></image>
				</button>
			</view>
		
		</view>
		
		<view class="wean">
			<text style="font-size: 150%;">注意：</text>
			Google搜索、Google学术搜索、中文维基百科需要科学上网 <br>
			更新预告：接下来要更新深色模式
		</view>
		
		<view class="footer">
			Copyright@2023-2026   WangSyutung
			<span>导航版本：v1.0.1 ALPHA</span>
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				url: '../../static/biglogo.png', 
				inputText: '',
				current: 1,
				items: [{
						name: 'Google搜索',
						value: 'gg'
					},
					{
						name: '百度搜索',
						value: 'bd'
					},
					{
						name: '必应搜索',
						value: 'bing'
					},
					{
						name: '谷歌学术搜索',
						value: 'ggxs'
					},
					{
						name: '中文维基百科',
						value: 'zhwiki'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			onBindSearch(e){
				console.info(e)
				
			},
			
			onGoogle(e) {
				console.info(e)
				console.info(this.$data.items[this.$data.current])
				console.info(this.$data.inputText)
				var text = this.$data.inputText
				var mode = e.currentTarget.dataset.mode
				if (mode === 'gg'){
					location.href="https://www.google.com/search?q="+text
				} else if (mode === 'bd'){
					location.href="https://www.baidu.com/s?wd="+text
				}  else if (mode === 'bing'){
					location.href="https://cn.bing.com/search?q="+text
				}  else if (mode === 'ggxs'){
					location.href="https://scholar.google.cz/scholar?q="+text
				} else if (mode === 'zhwiki'){
					location.href="https://zh.wikipedia.org/w/index.php?search="+text
				} 
				
			},
			onInput(e) {
				console.info(e)
				this.$data.inputText = e.detail.value
			},
			radioChange: function(evt) {
				for (let i = 0; i < this.items.length; i++) {
					if (this.items[i].value === evt.detail.value) {
						this.current = i;
						break;
					}
				}
			}
		}
	}
</script>

<style>
	page {
		width: 100%;
		box-sizing: border-box;
	}
	.com{
		margin: 5px;
		width:200px;
		display: flex;
		flex-direction: row;
		align-items: center;
		text-align: center;
		justify-content: center;
	}
	.wean{
		display: flex;
		flex-direction: column;
		width: 80%;
		box-sizing: border-box;
		align-self: center;
		padding: 20px; 
		border-radius: 20%;
		margin-bottom: 10%;
	}
	.footer{
		margin-bottom: 10%;
		text-align: center;
		align-items: center;
		display: flex;
		flex-direction: column;
		width: 100%;
		box-sizing: border-box;
	}
	.uni-list {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		margin-top: 20px;
		width: 100%;
		align-items: center;
		justify-content: center;
		text-align: center;

	}

	.font {
		width: 100%;
		font-size: 200%;
		font-weight: bold;
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
	}

	.btn {
		width: 30%;
		background-color: aquamarine;
		border: solid black;
		font-size: 20px;
		border-width: 1px;
		margin: 10px;
		border-radius: 30px;
		align-items: center;
	}

	.search {
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 100%;

		justify-content: center;
		padding: 10%;
		box-sizing: border-box;
		justify-self: center;
	}

	.input {
		margin: 10px;
		width: 100%;
		padding: 2%;
		font-size: 20px;
		border: solid black;
		border-width: 1px;
		border-radius: 30px;
		align-items: center;

	}

	.img {
		width: 100%;
		padding-left: 10%;
		box-sizing: border-box;
		padding-right: 10%;	
		
	}
	@media screen and  (orientation: landscape) {
	.img {
		width: 50%;
		padding-left: 10%;
		box-sizing: border-box;
		padding-right: 10%;	
		
	}
	}
	#app {
		margin-top: 60px;
		display: flex;
		flex-direction: column;
		width: 100%;
		box-sizing: border-box;

	}
</style>
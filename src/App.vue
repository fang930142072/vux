<template>
	<div id="app">
		<header ref="header" id="head">
			<img class="head_bg" src="./assets/bg_b1.png" alt="" />
			<!--返回-关注-->
			<div class="h clearfix">
				<div class="hl fl">
					<img src="./assets/icon-back.png" alt="" />
				</div>
				<div class="hr fr clearfix">
					<div class="fl">
						<img src="./assets/icon-follow.png" alt="" />
					</div>
					<span class="fl">关注</span>
				</div>
			</div>
			<!--球员logo名字部分-->
			<div class="nb">
				<div class="nbc clearfix">
					<!--<div class="logo fl">
							<img src="./assets/logo-team.png" alt="" />
						</div>-->
					<div class="img">
						<!--<img src="" alt="" />-->
						<div></div>
						<h4>球队名</h4>
						<!--<p>name name</p>-->
					</div>
					<!--<div class="qy fl">
							<img src="./assets/pic3.png" alt="" />
							<p>23</p>
						</div>-->
				</div>
			</div>
		</header>
		<!--<div style="height:44px;">
      <sticky scroll-box="vux_view_box_body" ref="sticky" :offset="46" :check-sticky-support="false">
        <tab :line-width="1">
          <tab-item selected>正在正映</tab-item>
          <tab-item>即将上映</tab-item>
        </tab>
      </sticky>
    </div>-->
		<div id="tabID">
			<tab :line-width=2 active-color='#bd1f26' v-model="index">
				<tab-item class="vux-center" :selected="listName === item.name" v-for="(item, index) in list" @click="listName = item.name" :key="index">{{item.name}}</tab-item>
			</tab>
			<!--<div style="height:1.75rem;">
      <sticky scroll-box="vux_view_box_body" ref="sticky" :offset="46" :check-sticky-support="false">
        			<tab :line-width=2 active-color='#bd1f26' v-model="index">
				<tab-item class="vux-center" :selected="listName === item.name" v-for="(item, index) in list" @click="listName = item.name" :key="index">{{item.name}}</tab-item>
			</tab>
      </sticky>
    </div>-->

						<div class="" :style="{height:touchs.top.distance+'px',lineHeight:touchs.top.distance+'px'}">
				<inline-loading></inline-loading><span v-text="touchs.top.loadReminder"></span></div>
			<swiper v-model="index" height="300px" ref="swiper" :show-dots="false" :threshold="100">
				<swiper-item>
					<div :class="{loading:true,dn:list[0].loading}">
						<load-more tip="正在加载"></load-more>
					</div>
					<div class="agenda tabLis">
						<div v-for="item in agenda">
							<div class="years">{{ item.years }}</div>
							<ul>
								<li class="clearfix" v-for="list in item.data">
									<div class="time">
										<span>{{ list.time }}</span>
									</div>
									<div class="nameL">
										<span>{{ list.nameL }}</span>
									</div>
									<div class="Lpic">
										<div></div>
									</div>
									<div class="vs">VS</div>
									<div class="Rpic">
										<div></div>
									</div>
									<div class="nameR">
										<span>{{ list.nameR }}</span>
									</div>
								</li>
							</ul>
						</div>
					</div>
				</swiper-item>
				<swiper-item>
					<div :class="{loading:true,dn:list[1].loading}">
						<load-more tip="正在加载"></load-more>
					</div>
					<ul class="videoB tabLis">
						<li class="clearfix" v-for="item in videolist">
							<div class="videoL fl">
								<img class="pic" :src="item.pic" alt="" />
								<img class="play" src="./assets/icon-play.png" alt="" />
							</div>

							<div class="videoR fl">
								<h3>{{ item.title }}</h3>
								<div class="clearfix">
									<span class="fl">{{ item.time }}</span>
									<div class="fr">
										<img src="./assets/icon-view.png" alt="" />
										<span>{{ item.comments }}</span>
									</div>
								</div>
							</div>
						</li>
					</ul>
					<!--<div :class="[listLoad,load]">加载数据</div>-->
					<!--<div :class="[load]">加载数据</div>-->
					<!--<load-more tip="正在加载" :class="[load]"></load-more>-->
					<!--<inlineloading :class="[load]">正在加载</inlineloading>-->
					<div :class="[load]">
						<inline-loading></inline-loading>正在加载</div>

				</swiper-item>
				<swiper-item>
					<div :class="{loading:true,dn:list[2].loading}">
						<load-more tip="正在加载"></load-more>
					</div>
					<div id="" class="player tabLis">
						<div class="head">球队信息</div>
						<ul class="message clearfix">
							<li class="fl">1886年成立</li>
							<li class="fl">主场：酋长球场</li>
							<li class="fl">英国伦敦</li>
							<li class="fl">容纳:303000人</li>
							<li class="fr">官网：www.baidu.com</li>
							<li class="fr">网址：www.baidu.com</li>
						</ul>
						<div class="head">教练组</div>
						<ul class="coach clearfix">
							<li class="fl clearfix">
								<div class="fl pic">
									<img src="#" alt="" />
								</div>
								<div class="fl name">
									<span>教练名</span>
									<p>主教练</p>
								</div>
							</li>
							<li class="fl clearfix">
								<div class="fl pic">
									<img src="#" alt="" />
								</div>
								<div class="fl name">
									<span>教练名</span>
									<p>副教练</p>
								</div>
							</li>
						</ul>
						<!--球员-->
						<ul class="footballer">
							<li>
								<div class="head clearfix">
									<div class="fl headD">前锋</div>
									<div class="fl tc">号码</div>
									<div class="fl tc">进球</div>
								</div>
								<div class="list">
									<div class="fl clearfix listD">
										<div class="fl"><img src="#" alt="" /></div>
										<span class="fl">球员名球队名</span>
									</div>
									<div class="fl tc">7</div>
									<div class="fl tc">30</div>
								</div>
							</li>
							<li>
								<div class="head clearfix">
									<div class="fl headD">前锋</div>
									<div class="fl tc">号码</div>
									<div class="fl tc">进球</div>
								</div>
								<div class="list">
									<div class="fl clearfix listD">
										<div class="fl"><img src="#" alt="" /></div>
										<span class="fl">球员名球队名</span>
									</div>
									<div class="fl tc">7</div>
									<div class="fl tc">30</div>
								</div>
							</li>
							<li>
								<div class="head clearfix">
									<div class="fl headD">前锋</div>
									<div class="fl tc">号码</div>
									<div class="fl tc">进球</div>
								</div>
								<div class="list">
									<div class="fl clearfix listD">
										<div class="fl"><img src="#" alt="" /></div>
										<span class="fl">球员名球队名</span>
									</div>
									<div class="fl tc">7</div>
									<div class="fl tc">30</div>
								</div>
							</li>
						</ul>
					</div>
				</swiper-item>
				<swiper-item>
					<div :class="{loading:true,dn:list[3].loading}">
						<load-more tip="正在加载"></load-more>
					</div>
					<div class="second tabLis">
						<div class="head">转入球员</div>
						<table class="shiftTo" border="" cellspacing="0" cellpadding="">
							<tr class="th">
								<th>
									<div>时间</div>
								</th>
								<th>
									<div>球员</div>
								</th>
								<th>
									<div>位置</div>
								</th>
								<th>
									<div>来自</div>
								</th>
								<th>
									<div>类型</div>
								</th>
							</tr>
							<tr>
								<td>2017-7-7</td>
								<td>球员名球员名球员名球员名</td>
								<td>后卫</td>
								<td>里昂</td>
								<td>自由转会</td>
							</tr>
						</table>
						<div class="head">转入球员</div>
						<table class="rollOut" border="" cellspacing="0" cellpadding="">
							<tr class="th">
								<th>
									<div>时间</div>
								</th>
								<th>
									<div>球员</div>
								</th>
								<th>
									<div>位置</div>
								</th>
								<th>
									<div>来自</div>
								</th>
								<th>
									<div>类型</div>
								</th>
							</tr>
							<tr>
								<td>2017-7-7</td>
								<td>球员名球员名球员名球员名球员名</td>
								<td>后卫</td>
								<td>里昂</td>
								<td>自由转会</td>
							</tr>
						</table>
					</div>
				</swiper-item>
			</swiper>
		</div>
		<!--<scroller lock-x height="200px" @on-scroll-bottom="onScrollBottom" ref="scrollerBottom" :scroll-bottom-offst="200">
      <div class="box2">
        <p v-for="i in 50">placeholder {{i}}</p>

      </div>
    </scroller>-->
<!--
		<div>{{ start }}</div>

		<div>{{ move }}</div>
		<div>{{ distance }}</div>-->

	</div>
</template>

<script>
	import { Tab, TabItem, Swiper, SwiperItem, LoadMore, Scroller, InlineLoading } from 'vux'
	export default {
		components: {
			Tab,
			TabItem,
			Swiper,
			SwiperItem,
			LoadMore,
			Scroller,
			InlineLoading
		},
		data() {
			return {
				list: [{
					name: '赛程',
					loading: false
				}, {
					name: '视频',
					loading: false
				}, {
					name: '球员',
					loading: false
				}, {
					name: '转会',
					loading: false
				}],
				listName: '赛程',
				height: '180px',
				index: 0,
				loading: true,
				listLoad: 'dn',
				load: 'listLoad',
				fullscreenLoading: true,
				videolist: [{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					},
					{
						pic: 'static/pic4.png',
						title: '视频标题',
						time: '3天前',
						comments: 999
					}
				],
				agenda: [{
					years: '2017-07-22 星期六',
					data: [{
						time: '06:00 am',
						nameL: "球队名球队名球队名球队名",
						nameR: "球队名",
						picL: "",
						picR: ""
					}, {
						time: '06:00 am',
						nameL: "球队名球队名球队名球队名",
						nameR: "球队名",
						picL: "",
						picR: ""
					}]
				}, {
					years: '2017-07-22 星期六',
					data: [{
						time: '06:00 am',
						nameL: "球队名球队名球队名球队名",
						nameR: "球队名",
						picL: "",
						picR: ""
					}, {
						time: '06:00 am',
						nameL: "球队名球队名球队名球队名",
						nameR: "球队名",
						picL: "",
						picR: ""
					}]
				}],
				scrollTop: this.onScroll(),
				datumList: [
					[
						['身高', '180cm'],
						['体重', '76kg'],
						['生日', '1988-10-15'],
						['国籍', '德国']
					],
					[
						['球队', '阿纳森'],
						['球号', '11'],
						['位置', '前锋/后卫'],
						['预计身价', '4250万英镑']
					]
				],
				footballer: [
					['个人简介', '厄齐尔是鲁尔区的孩子。。。。'],
					['俱乐部生涯', '1995年, 他在威斯特法亚跨出了自己篮球场的第一步第一步第一步第一步第一步。。。。'],
					['国家队履历', ''],
					['国家队履历', ''],
					['国家队履历', ''],
					['国家队履历', ''],
					['国家队履历', ''],
					['国家队履历', ''],
					['国家队履历', '']
				],
				touchs: {
					top: {
						start: 0,
						move: 0,
						end: 0,
						distance: 0,
						loadReminder: '下拉刷新'
					},
					bottom: {
						start: 0,
						move: 0,
						end: 0,
						distance: 0,
						loadReminder: '下拉刷新'
					}
				}
			}
		},
		methods: {
			//tab栏切换改变容器高
			change(val, oldval) {
				var This = this;
				var vuxTab = document.getElementsByClassName('vux-tab')[0];
				var tabLis = document.getElementsByClassName('tabLis')[this.index];
				if(This.list[val].loading == false) {
					//						document.getElementsByClassName('vux-swiper-item')[val].style.height = '300px'
					setTimeout(() => {
						document.getElementsByClassName('vux-swiper-item')[val].style.height = '100%'
						this.$refs.swiper.xheight = tabLis.offsetHeight +vuxTab.offsetHeight + "px"
						//						document.getElementsByClassName('vux-swiper')[0].style.height = document.getElementsByClassName('tabLis')[this.index].offsetHeight + "px"
						This.list[val].loading = 'true'
					}, 1000)
				}
				this.$refs.swiper.xheight = tabLis.offsetHeight +vuxTab.offsetHeight + "px"
				//				document.getElementsByClassName('vux-swiper')[0].style.height = document.getElementsByClassName('tabLis')[this.index].offsetHeight + "px"

				//				document.getElementsByClassName('vux-swiper')[0].style.height = document.getElementsByClassName('tabLis')[this.index].offsetHeight+
				//									document.getElementsByClassName('vux-tab')[0].offsetHeight/2 + "px"

				//				console.log(document.getElementsByClassName('tabLis')[this.index].offsetHeight)
				//				this.height = document.getElementsByClassName('tabLis')[this.index].offsetHeight+'px'

				//		console.log(val,oldval)
				//		console.log(This.list)
				//		console.log(This.index)
			},
			handleClick(tab, event) {
				//				console.log(tab, event);
			},
			onScroll(e, p) {
				var This = this;
				var Window = window;
				window.addEventListener('scroll', function() {
						//						console.log(document.body.scrollTop)
						//						console.log(document.getElementById('head').offsetHeight)
						var elHeader = document.getElementsByClassName('vux-tab')[0];
						var header = document.getElementById('head');
						if(document.body.scrollTop >= header.offsetHeight) {
							elHeader.style.position = "fixed";
							elHeader.style.top = "0px";
							elHeader.style.width = "100%";
							elHeader.style.zIndex = "100";
							header.style.marginBottom = elHeader.offsetHeight + "px";
						} else {
							elHeader.style.position = "relative";
							elHeader.style.top = "none";
							header.style.marginBottom = "0px";
						}
					}

				);
			},
			menu() {
				let scr = document.body.scrollTop + window.screen.availHeight;
				if(document.body.offsetHeight - document.getElementsByClassName('listLoad')[0].offsetHeight == scr) {
					//		        	console.log(this.index)
					if(this.index == 1) {
//						console.log('底部')
						this.listLoad = '';

						document.getElementsByClassName('vux-swiper')[0].style.height =
							document.getElementsByClassName('tabLis')[this.index].offsetHeight +
							document.getElementsByClassName('vux-tab')[0].offsetHeight +
							"px"
					}
				}

			},
			//触摸事件
			touch(event) {
				var event = event || window.event;
				var tabId = document.getElementById('tabID');
				var bodyH = document.body.scrollTop + window.screen.availHeight;
				var place = '';
										if(document.body.scrollTop == 0){
//											console.log("top")
											place = 'top'
											this.tuochList(event,place)
										}else if(bodyH == document.body.offsetHeight){
//											console.log("bottom")
											
											place = 'bottom'
											this.tuochList(event,place)
											
										}
//				bodyH == document.body.offsetHeight




			},
			tuochList(event,place){
									switch(event.type) {
						case "touchstart":
//console.log('touchstart')

							this.touchs[place].start = event.touches[0].clientY;

							//						console.log("touchstart", event.touches[0].clientY);
							break;

						case "touchmove":
//console.log('touchmove')
						
							this.touchs[place].move = event.touches[0].clientY;
							var distanceN =this.touchs[place].start-event.touches[0].clientY;
							if(place == 'top'&&distanceN<0){
								distanceN = -distanceN;;
//								console.log('top','true')
								
							}else if(place == 'top'&&distanceN>0){
								distanceN = 0;
//								console.log('top','false')
								
								
							}else if(place == 'bottom'&&distanceN>50){
								distanceN = distanceN;;
//								console.log('bottom','true')
//								if(distanceN>50){
									distanceN = 51
//								}
								
							}else{
								distanceN = distanceN;
								if(distanceN<50){
								distanceN = 0;
									
								}
//								console.log('bottom','false')
								
							}
							this.touchs[place].distance = distanceN;
							
							if(distanceN > 50) {
								this.touchs[place].loadReminder = '松开刷新';
							}
							//						console.log("touchmove", event.touches[0].clientY);
							break;
						case "touchend":
//						default :
//console.log('touchend')

							this.touchs[place].end = event.changedTouches[0].clientY;
//							console.log(this.touchs[place].distance)
							var distance = this.touchs[place].distance;
							//							var bottom = this.touchs[place].distance < -50 && bodyH == document.body.offsetHeight;
							var top = distance > 50;
							var bottom = distance < -50;
//							console.log(top,bottom)
//							console.log(distance)
							if(top || bottom){
//								tabId.removeEventListener('touchstart', this.touch, false);
//								tabId.removeEventListener('touchmove', this.touch, false);
//								tabId.removeEventListener('touchend', this.touch, false);
								this.touchs[place].loadReminder = "正在刷新,请稍后"
								
//								if(top){
									this.touchs[place].distance = 50;
//								}else if(bottom){
//									this.touchs[place].distance = -50;
//								}
							}else {
								this.touchs[place].distance = 0;
							}
							break;

					}
			}
			//			,switchover(dom) {
			//				this.fullscreenLoading = true;
			//				setTimeout(() => {
			//					this.fullscreenLoading = false;
			//					document.getElementsByClassName(dom)[0].className = 'tabLis ' + dom + ' showB';
			//
			//				}, 1000);
			//				let tabLi = document.getElementsByClassName('tabLi');
			//				for(let i = 0; i < tabLi.length; i++) {
			//					document.getElementsByClassName(dom)[0].className = 'tabLis ' + dom;
			//					tabLi[i].className = 'tabLi';
			//				}
			//				document.getElementById(dom).className = 'tabLi show';
			//			}
		},
		watch: {
			index: 'change'
		},
		mounted: function() {
			//初始化加载
			this.change(this.index)
//			tab滚动事件
			window.addEventListener('scroll', this.menu);
			//下拉加载触摸事件
			var tabId = document.getElementById('tabID');
			tabId.addEventListener('touchstart', this.touch, false);
			tabId.addEventListener('touchmove', this.touch, false);
			tabId.addEventListener('touchend', this.touch, false);
		}
	}
</script>

<style lang="less" scoped>
	@import '~vux/src/styles/1px.less';
	@import '~vux/src/styles/center.less';
	@import url("./style/reset.css");

	.trans{}
.vux-slider>.vux-swiper{overflow:auto;height:auto!important}
.loading{position:absolute;top:0;left:0;width:100%;height:100%;background:#fff;z-index:50}
.listLoad{height:1.75rem;font-size:.5rem;line-height:1.75rem}
.dn{display:none!important}
#app{font-family:'Avenir',Helvetica,Arial,sans-serif;-webkit-font-smoothing:antialiased;-moz-osx-font-smoothing:grayscale;text-align:center;color:#2c3e50}
.tabLi{display:none}
.show{display:block!important;position:relative}
.showB{display:block!important;height:auto!important;overflow:auto!important}
.tabLi>div,.tabLi>ul{display:none}
.demo-spin-icon-load{animation:ani-demo-spin 1s linear infinite}
@keyframes ani-demo-spin{from{transform:rotate(0deg)}
50%{transform:rotate(180deg)}
to{transform:rotate(360deg)}
}.demo-spin-col{height:100px;position:relative;border:1px solid #eee}
.modal{height:100%;width:100%;position:fixed;top:0;left:0;background:#fff;z-index:20}
.ivu-icon{font-size:2rem!important}
.ivu-spin-text>div{padding:1rem 0;font-size:1.5rem}
header{height:8.5rem;position:relative;overflow:hidden;.head_bg{position:absolute;top:0;left:0;width:100%;height:100%}
.h{height:1.1rem;padding:0 0.5rem;margin-top:0.75rem;position:relative;.hl{img{height:100%}
height:100%}
.hr{color:#00aeff;font-size:0.45rem;height:1.1rem;line-height:1.1rem;font-weight:bold;div.fl{height:100%}
div img{vertical-align:middle;margin:0px 0.2rem;height:.8rem;margin-top:.1rem}
span{font-size:.5rem;height:.8rem;line-height:.8rem;margin-top:.23rem}
}}.nb{position:relative;margin:1rem auto 0 auto;color:#fff;text-align:center;.nbc{display:inline-block}
.img{margin:0 1.5rem;div{width:3rem;height:3rem;background:#fff;border-radius:50%}
h4{padding:0.6rem 0;font-size:0.5rem;line-height:1em}
p{line-height:1em;font-size:0.45rem}
}}}
.agenda{.years{height:1rem;line-height:1rem;text-align:center;color:#333;background:#E0E0E0;font-size:0.45rem}
ul{background:#fff}
li{height:2.625rem;border-bottom:1px solid #eee;width:100%;padding:0 0.4rem;font-size:0.45rem;>div{float:left;height:2.625rem;line-height:2.625rem}
.time{width:2rem;line-height:1em}
.nameL{margin-left:1rem;width:3rem;padding-bottom:0}
.Lpic{width:1.5rem;margin-left:0.5rem}
.vs{padding:0 .625rem}
.Rpic div,.Lpic div{width:1.5rem;height:1.5rem;display:inline-block;border-radius:50%;background:#bababa;margin-top:0.5rem}
.nameL,.nameR,.time{line-height:1em;line-height:0.75rem;position:relative;span{position:absolute;top:50%;left:0;width:100%;transform:translateY(-50%)}
}.nameR{width:3rem}
.Rpic{width:1.5rem;margin-right:0.5rem}
}}ul.videoB li{list-style:none;height:5.5rem;padding:0.75rem 0.5rem;border-bottom:1px solid #eee;background:#fff;.videoL{height:4rem;width:5.5rem;position:relative;margin-right:0.75rem;.play{position:absolute;width:1.75rem;height:1.75rem;top:50%;left:50%;transform:translate(-50%,-50%)}
.pic{width:100%;height:100%}
}.videoR{width:8.5rem;height:100%;position:relative;h3{font-size:0.5rem;text-align:left}
.clearfix{position:absolute;bottom:0;width:100%;height:0.525rem;line-height:0.525rem;font-size:0.45rem;.fr{color:#00aeff;img{height:0.525rem}
}}}
}ul.datum{padding:0 0.5rem;background-color:#fff;li{border-bottom:1px solid #eee;height:1.5rem;line-height:1.5rem;font-size:0.45rem}
}.interval{height:0.5rem}
.footballer{text-align:left;h2{height:1.5rem;line-height:1.5rem;padding-left:.5rem;font-size:0.5rem;font-weight:400}
ul{padding:.5rem;background:#fff;padding-bottom:.75rem;li{margin-bottom:.75rem;h3{line-height:1rem;font-weight:normal;font-size:0.45rem}
p{line-height:1.125rem;font-size:0.45rem;text-indent:2em}
}}}
.player{.head{height:1.5rem;line-height:1.5rem;padding-left:0.625rem;font-size:0.625rem;background:#d9d9d9;text-align:left}
.message{padding:0.625rem;li{height:1rem;line-height:1rem;font-size:0.45rem}
.fl{width:50%;text-align:left}
.fr{text-align:left;width:100%}
}.coach{padding-left:0.625rem;height:3rem;li{width:50%;height:100%;.pic{height:100%;img{width:1.5rem;height:1.5rem;border-radius:50%;background:#E0E0E0;margin-top:0.75rem}
}.name{margin-top:0.75rem;margin-left:0.5rem;span{font-size:0.45rem;font-weight:bold;line-height:.8rem}
p{color:#919191;text-align:left;font-size:0.45rem;line-height:.7rem}
}}}
}.footballer{.head{background:#D9D9D9;height:1.5rem;line-height:1.5rem;padding-left:0.5rem;padding-right:0.5rem}
.head,.list{>div{width:30%;text-align:left;font-size:0.45rem;padding-left:0.5rem}
.headD{width:40%}
.listD{width:40%}
.tc{text-align:center}
.tr{text-align:right}
}.list{height:2.85rem;line-height:2.85rem;padding-left:0.5rem;padding-right:0.5rem;img{border-radius:50%;width:1.5rem;height:1.5rem;background:#E0E0E0}
span{padding-left:0.3rem}
}}.second{.head{height:1.5rem;line-height:1.5rem;padding-left:0.625rem;font-size:0.625rem;background:#d9d9d9;text-align:left}
table{border-collapse:collapse;width:100%;border:0;tr{border-bottom:1px solid #ddd}
th{height:1.5rem;font-size:0.45rem;border:0;width:3.25rem;div{height:1rem;line-height:1rem;border-right:1px solid #ddd;margin-top:0.25rem}
&:last-child div{border:0}
}td{width:3.25rem;height:1.75rem;font-size:0.45rem;border:0}
}}.weui-loadmore{top:50%}
.vux-tab{height:1.75rem}
.vux-tab .vux-tab-item{height:1.75rem;line-height:1.75rem;font-size:0.625rem}
.vux-slider>.vux-swiper>.vux-swiper-item{overflow:hidden;height:300px}
	

	
</style>
---
layout: category
title: Personal
---
<script src="https://cdn.staticfile.org/jquery/1.12.4/jquery.min.js"></script><!--引入jquery-->
<style>
p.ex1 {margin-bottom:0.2cm}
</style>
<p><t1><big><em> You may find something interesting about me in this page.</em></big></t1></p>
<br>
<t-half><strong>Memory</strong></t-half>
<p class="ex1"><t1>Could u recognize me from the photos?</t1></p>
<p>
<table border="0">
<tbody>
<tr>
<img src="https://csyhquan.github.io/images/The_first_Guangzhou_Elite_Project.jpg" alt="" height="265" class="pimg"/>
</tr>
</tbody>
</table>
<table border="0">
<tbody>
<tr>
<img src="https://csyhquan.github.io/images/Pearl_River(2020.11.19).jpg" alt="" height="260" class="pimg"/>
<img src="https://csyhquan.github.io/images/personal_1.png" alt="" height="260" class="pimg"/>
<img src="https://csyhquan.github.io/images/personal_2.png" alt="" height="260" class="pimg"/>
</tr>
</tbody>
</table>
</p>
<br>
<t-half><strong>Writing</strong></t-half>
<p><t1>One of my favorite hobbies is writing ancient Chinese poems. Some of my works can be found <a href="https://csyhquan.github.io/category/poem/poem.html">here</a>. <br />I also wrote a <a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/category/poem/PoemAssist.rar">program</a> for checking the rhythm errors of a ancient Chinese poem and assisting the writing.</t1></p>
<br>

<t-half><strong>Just for Fun</strong></t-half>
<p><t1>I made some mini games when I was a student. Sometimes I use them to relax myself when the research is stuck. Hope they can serve you as well. <br />Unluckily, no readme files could be provided currently for the games. You may have to explore the rules and runtime installations by yourself.<br>
[<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/War%20of%20Tank.rar">War of Tanks</a>] [<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/EndlessMaze.rar">Endless Maze</a>] [<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/SuperCards_HvsH.rar">Super Cards (Human VS Human)</a>] [<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/SuperCards_HvsC.rar">Super Cards (Human VS COM)</a>] [<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/Bricks.rar">Bricks</a>] [<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/Helicopter.rar">Helicopter</a>] [<a href="https://github.com/csyhquan/csyhquan.github.io/raw/master/games/Phoenix.rar">Phoenix</a>].
</t1></p>
<br>
<t-half><strong>Toys</strong></t-half>
<p class="ex1">
<t1>Texture removal on my son’s baby play mat, based on our upcoming work.</t1></p>
<p>
<img src="https://csyhquan.github.io/images/personal_3.png" alt="" height="390" class="pimg"/>
</p>
<!--Jquery代码，用于放大图片-->
<div id="outerdiv" style="position:fixed;top:0;left:0;background:rgba(0,0,0,0.7);z-index:2000;width:100%;height:100%;display:none;">
	<!-- 放大后的图片 -->
	<div id="innerdiv" style="position:absolute;z-index: 2000">
		<img id="bigimg" style="border:0px solid #fff;" src="" />
	</div>
</div>
<script>
    // 图片点击事件
	$('.pimg').click(function () {
		enlarge(this);
	})

	// 图片放大函数
	function enlarge(obj) {

		var _this = $(obj);
		imgShow("#outerdiv", "#innerdiv", "#bigimg", _this);


		function imgShow(outerdiv, innerdiv, bigimg, _this) {
			var src = _this.attr("src"); //获取当前点击的pimg元素中的src属性  
			$(bigimg).attr("src", src); //设置#bigimg元素的src属性  

			/*获取当前点击图片的真实大小，并显示弹出层及大图*/
			$("<img/>").attr("src", src).load(function () {
				var windowW = $(window).width(); //获取当前窗口宽度  
				var windowH = $(window).height(); //获取当前窗口高度  
				var realWidth = this.width; //获取图片真实宽度  
				var realHeight = this.height; //获取图片真实高度  
				var imgWidth, imgHeight;
				var scale = 0.8; //缩放尺寸，当图片真实宽度和高度大于窗口宽度和高度时进行缩放  

				if (realHeight > windowH * scale) { //判断图片高度  
					imgHeight = windowH * scale; //如大于窗口高度，图片高度进行缩放  
					imgWidth = imgHeight / realHeight * realWidth; //等比例缩放宽度  
					if (imgWidth > windowW * scale) { //如宽度扔大于窗口宽度  
						imgWidth = windowW * scale; //再对宽度进行缩放  
					}
				} else if (realWidth > windowW * scale) { //如图片高度合适，判断图片宽度  
					imgWidth = windowW * scale; //如大于窗口宽度，图片宽度进行缩放  
					imgHeight = imgWidth / realWidth * realHeight; //等比例缩放高度  
				} else { //如果图片真实高度和宽度都符合要求，高宽不变  
					imgWidth = realWidth;
					imgHeight = realHeight;
				}
				$(bigimg).css("width", imgWidth); //以最终的宽度对图片缩放  

				var w = (windowW - imgWidth) / 2; //计算图片与窗口左边距  
				var h = (windowH - imgHeight) / 2; //计算图片与窗口上边距  
				$(innerdiv).css({
					"top": h,
					"left": w
				}); //设置#innerdiv的top和left属性  
				$(outerdiv).fadeIn("fast"); //淡入显示#outerdiv及.pimg  
			});

			$(outerdiv).click(function () { //再次点击淡出消失弹出层  
				$(this).fadeOut("fast");
			});
		}
	}
</script>
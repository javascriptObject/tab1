# js和jq选项目卡
* 效果如下

![](images/img.gif)

* HTML&CSS代码如下
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>选项卡</title>
	<style>
	ul{list-style: none}
		ul.tad li{float: left;margin-left: 10px;border:1px solid #ddd;}
		ul.tad{overflow: hidden}
		ul.tad li.active{background: red;}
		ul.con li{width: 200px;height: 100px;background: #abcdef;display: none;}
		ul.con li.show{display: block;}
	</style>
</head>
<body>
	<ul class="tad">
		<li class="active">热门活动</li>
		<li>猜你喜欢</li>
	</ul>
	<ul class="con">
		<li class="show">11111</li>
		<li>22222</li>
	</ul>
</body>
</html>
```
* js代码下如
```
	 window.onload = function(){
	 	var oTad = document.getElementsByClassName("tad")[0];
	 	var oLi = oTad.getElementsByTagName("li");
	 	var oCon = document.getElementsByClassName("con")[0];
	 	var oLi2 = oCon.getElementsByTagName("li");
	 	for(var i=0;i<oLi.length;i++){
	 		oLi[i].index = i;
	 		oLi[i].onclick = function(){
	 			for(var i=0;i<oLi.length;i++){
	 				oLi[i].className = "";
	 				oLi2[i].style.display = 'none';
	 			}
	 			this.className = "active";
	 			oLi2[this.index].style.display = 'block';
	 		}
	 	}
	 };
```
* 或jQuery代码如下
```
	$(function(){
		$('ul.tad li').click(function(){
			$('ul.tad li').attr('class','');
			$('ul.con li').css('display','none');
			$(this).attr('class','active');
			$('ul.con li').eq($(this).index()).css('display','block');
		});
	})
```

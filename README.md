<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<title>mouse coordinates jq</title>
<style>
	html, body {
		width: 100%;
		height: 100%;
		padding: 0;
		margin: 0;
	}
	body {
		background-color: rgba(100,100,100,0.2);
		overflow: hidden;
	}

	#wrapper {
		width: 100%;
		min-height: 100%;
		margin: 0 auto;
		position: relative;
	}

	#pp {
		width: 100px;
		height: 100px;
		background-color: rgba(100,0,0,0.3);
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
	}

	svg {
		outline: 1px solid blue;
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
		width: 100%;
		height: 100%;
	}
</style>
</head>

<body>
	<div id="wrapper">
		<div id="status1"></div>
		<div id="status2"></div>
		<div id="pp"></div>
		<svg id="mysvg" height="400" width="450"></svg>
	</div><!--/#wrapper-->
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
	
	<script>
		$(document).ready(function(){
			var d = document;
			var mysvg = d.getElementById("mysvg");

			//$("#status1").html("<strong>svg size</strong><br>width: " + svgw + "<br>height: " + svgh);

			//mouse position
			var m = {'x':0, 'y':0};
			$(document).on('mousemove', function(e) {
				m = {'x': e.clientX, 'y': e.clientY};
			});

			$(function(){
				setInterval(function() {
				//svg width and height
				var svgw = $("svg").width();
				var svgh = $("svg").height();

				//initial pt
				var mdpt = svgw/2;
				var yini = svgh - 100;

				//random numbers
				var rand = {
					aa: Math.floor(Math.random()*100),
				};

				var input1 = '<path d="M ' + mdpt + ' ' + yini + 
									 ' L ' + m.x + ' ' + m.y +
									 '" stroke="orange" stroke-width="7" stroke-linejoin="round" fill="none" />';

				$("#mysvg").html(input1);

				$("#status2").html("<strong>svg size</strong><br>width: " + svgw + "<br>height: " + svgh + "<br><br><strong>mouse position</strong><br>X coordinate: " + m.x + "<br> Y coordinate: " + m.y + "<br><br><strong>random numbers</strong><br>" + rand.aa);
				}, 1000);
			});
		});
	</script>
	<!--
	<script>
		$(document).ready(function(){
			var d = document;
			var mysvg = d.getElementById("mysvg");

			setInterval(function(){
				var rand_global = {
					aa: Math.floor(Math.random()*100)
				};
				$("#status2").html(rand_global.aa);
			}, 10);

			mysvg.addEventListener("mousemove", myFunction1);

			function myFunction1(e) {
				//svg width and height
				var svgw = $("svg").width();
				var svgh = $("svg").height();

				//aquire x and y coordinates relative to window size
				var mx = e.clientX;
				var my = e.clientY;

				//random numbers
				var rand = {
					aa: Math.floor(Math.random()*100),
				};
				
				$("#status1").html("<strong>svg size</strong><br>width: " + svgw + "<br>height: " + svgh + "<br><br>X coord: " + mx + "<br>Y coord: " + my + "<br><br>random local: " + rand.aa + "<br><br>random global: ");
			}
		});
	</script>
	-->
</body>
</html>

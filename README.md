1. Creating the Page Template

index.html
1	<!DOCTYPE html>
2	<html>
3	<head>
4	<meta charset="utf-8">
5	<title>Creating Popup Div | istockphp.com</title>
6	<link href="style/style.css" rel="stylesheet" type="text/css" media="all" />
7	<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"> </script>
8	<script type="text/javascript" src="js/script.js"></script>
9	</head>
10	 
11	<body>
12	    <a href="#" class="topopup">Click Here Trigger</a>
13	 
14	    <div id="toPopup">
15	 
16	        <div class="close"></div>
17	        <span class="ecs_tooltip">Press Esc to close <span class="arrow"></span></span>
18	        <div id="popup_content"> <!--your content start-->
19	            <p>netus et malesuada fames ac turpis egestas. </p>
20	            <p align="center"><a href="#" class="livebox">Click Here Trigger</a></p>
21	        </div> <!--your content end-->
22	 
23	    </div> <!--toPopup end-->
24	 
25	    <div class="loader"></div>
26	    <div id="backgroundPopup"></div>
27	</body>
28	</html>

In index.html, we include the css, jquery script and js script after the title tag; in the body we have 3 div containers for popup div event.

    div container for loading
    div container for popup background,
    and div container for popup

2. The stylesheet

style.css
1	#backgroundPopup {
2	    z-index:1;
3	    position: fixed;
4	    display:none;
5	    height:100%;
6	    width:100%;
7	    background:#000000;
8	    top:0px;
9	    left:0px;
10	}
11	#toPopup {
12	    font-family: "lucida grande",tahoma,verdana,arial,sans-serif;
13	    background: none repeat scroll 0 0 #FFFFFF;
14	    border: 10px solid #ccc;
15	    border-radius: 3px 3px 3px 3px;
16	    color: #333333;
17	    display: none;
18	    font-size: 14px;
19	    left: 50%;
20	    margin-left: -402px;
21	    position: fixed;
22	    top: 20%;
23	    width: 800px;
24	    z-index: 2;
25	}
26	div.loader {
27	    background: url("../img/loading.gif") no-repeat scroll 0 0 transparent;
28	    height: 32px;
29	    width: 32px;
30	    display: none;
31	    z-index: 9999;
32	    top: 40%;
33	    left: 50%;
34	    position: absolute;
35	    margin-left: -10px;
36	}
37	div.close {
38	    background: url("../img/closebox.png") no-repeat scroll 0 0 transparent;
39	    cursor: pointer;
40	    height: 30px;
41	    position: absolute;
42	    right: -27px;
43	    top: -24px;
44	    width: 30px;
45	}
46	span.ecs_tooltip {
47	    background: none repeat scroll 0 0 #000000;
48	    border-radius: 2px 2px 2px 2px;
49	    color: #FFFFFF;
50	    display: none;
51	    font-size: 11px;
52	    height: 16px;
53	    opacity: 0.7;
54	    padding: 4px 3px 2px 5px;
55	    position: absolute;
56	    right: -62px;
57	    text-align: center;
58	    top: -51px;
59	    width: 93px;
60	}
61	span.arrow {
62	    border-left: 5px solid transparent;
63	    border-right: 5px solid transparent;
64	    border-top: 7px solid #000000;
65	    display: block;
66	    height: 1px;
67	    left: 40px;
68	    position: relative;
69	    top: 3px;
70	    width: 1px;
71	}
72	div#popup_content {
73	    margin: 4px 7px;
74	    /* remove this comment if you want scroll bar
75	    overflow-y:scroll;
76	    height:200px
77	    */
78	}

In the css, if you want scrollbar in the popup just remove comment in line 74.
3. The jQuery script

script.js
1	jQuery(function($) {
2	 
3	    $("a.topopup").click(function() {
4	            loading(); // loading
5	            setTimeout(function(){ // then show popup, deley in .5 second
6	                loadPopup(); // function show popup
7	            }, 500); // .5 second
8	    return false;
9	    });
10	 
11	    /* event for close the popup */
12	    $("div.close").hover(
13	                    function() {
14	                        $('span.ecs_tooltip').show();
15	                    },
16	                    function () {
17	                        $('span.ecs_tooltip').hide();
18	                    }
19	                );
20	 
21	    $("div.close").click(function() {
22	        disablePopup();  // function close pop up
23	    });
24	 
25	    $(this).keyup(function(event) {
26	        if (event.which == 27) { // 27 is 'Ecs' in the keyboard
27	            disablePopup();  // function close pop up
28	        }
29	    });
30	 
31	        $("div#backgroundPopup").click(function() {
32	        disablePopup();  // function close pop up
33	    });
34	 
35	    $('a.livebox').click(function() {
36	        alert('Hello World!');
37	    return false;
38	    });
39	 
40	     /************** start: functions. **************/
41	    function loading() {
42	        $("div.loader").show();
43	    }
44	    function closeloading() {
45	        $("div.loader").fadeOut('normal');
46	    }
47	 
48	    var popupStatus = 0; // set value
49	 
50	    function loadPopup() {
51	        if(popupStatus == 0) { // if value is 0, show popup
52	            closeloading(); // fadeout loading
53	            $("#toPopup").fadeIn(0500); // fadein popup div
54	            $("#backgroundPopup").css("opacity", "0.7"); // css opacity, supports IE7, IE8
55	            $("#backgroundPopup").fadeIn(0001);
56	            popupStatus = 1; // and set value to 1
57	        }
58	    }
59	 
60	    function disablePopup() {
61	        if(popupStatus == 1) { // if value is 1, close popup
62	            $("#toPopup").fadeOut("normal");
63	            $("#backgroundPopup").fadeOut("normal");
64	            popupStatus = 0;  // and set value to 0
65	        }
66	    }
67	    /************** end: functions. **************/
68	}); // jQuery End

In the click event we triggered the loading() function and delay 0.5 second and triggered the loadPopup() function and the pop up displays. We add little more for closing the popup, if hover the ‘Close’ the tool tip message will appeared and keyboard event for close.
4. Done

We’re done, we learn one of jquery example on creating our own popup div using jQuery, and you can edit the content of the popup like adding more text, registration form and image. Let’s have a look at what we’ve achieved:

    We create popup div without third party plugin
    Works in old IE browser, IE 7,8
    We add little feature, hover tool tip and keyboard event

If you enjoyed this article, please consider sharing it!
- See more at: http://istockphp.com/jquery/creating-popup-div-with-jquery/#sthash.YFgFleao.dpuf

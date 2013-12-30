web----
=======
!function($){
	
	"use strict";       

	var Input = function(element,options){
		this.$element = $(element);
		this.options = $.extend({}, $.fn.input.defaults, options);
		this.value = "";
		var that = this;
		this.$element.on('blur',function(){
			that.check();
		});
	}
	
	Input.prototype.check = function(){
		var val = this.$element.val();
		if(this.options.vodtype == "telno"){
			var re=/^1[3][9]\d{8}$/;
			if (re.test(val))
		    alert("符合规定，vodtype is telephonenumber and it's value=" + val);
		  else{
		  	alert("不符合规定，vodtype is  NOT telephonenumber and it's value=" + val);
		  }
		}
		
		  else if(this.options.vodtype == "email"){
			
			var reMail = /^\w+@\w+\.\w+$/;
			if(reMail.test(val))
			   alert("符合规定，vodtype is Email and it's value=" + val);
      else{
		     alert("不符合规定，vodtype is  NOT Email and it's value=" + val);
		 }
		}
		
		else(this.options.vodtype == "normal")
			   
	}

	$.fn.input = function (option,param) {
		var result = null;
	    var input = this.each(function () {
	    	var $this = $(this)
	        	, data = $this.data('myinput')
	        	, options = typeof option == 'object' && option;
	    	if(typeof option == 'string' ){
	    		result = data[option](param);
	    	}else{
	    		$this.data('myinput', (data = new Input(this, options)));
	    	}
	    });
	    if(typeof option == 'string' )return result;
	    return input;
	};
	
	$.fn.input.defaults = {
		vodtype:'normal'
	};

	$(window).on('load', function(){
		$("[class='myinput']").each(function () {
			var $input = $(this)
			, data = $input.data('options');
			if(!data) return;
			$input.input((new Function("return {" + data + "}"))());
		});
	});
}(window.jQuery);


<!DOCTYPE html>
<html>
	<head>
		<title> INTEL| webÇ°¶Ë¿ª·¢Ð¡×é </title>
		</title>
	</head>
	<body bgcolor="CCFFFF">
		
		
		<div id="container">
    <div id="header" > <h1>INTEL | webÇ°¶Ë¿ª·¢</h1></div>
   <font color="000000" size="5" face="ËÎÌå"></font>
    <div id="mainContent"  style="text-align:center">
      <p><img src="test.jpg"  alt="pic"  width="1440" height="485"/></P>
      <hr></hr>
      
      <center>
      <td>
      <a href="http://www.channelsoft.com/" title="ÄãÊÇ´ó±¿µ°" id="a1">   Ê×Ò³  </a>
      <a href="http://www.channelsoft.com/productsandservices.jsp" title="ÔÙµãÄã¾ÍÊÇ´óÉµ¹Ï">  ²úÆ·Óë·þÎñ  </a>
      <a href="http://www.channelsoft.com/succproducts.jsp" title"ÎÒ¿´Äã»¹¸Òµã">  ³É¹¦°¸Àý  </a>
      <a href="http://www.channelsoft.com/news.jsp" title="ÔÙµã¾Í°ÑÄã³Ôµô">  INTEL try point  </a>
      <a href="http://www.channelsoft.com/join.jsp" title="ÄãÊÇ´ó¶ñÄ§">  Join us  </a>
      <a href="http://www.channelsoft.com/about.jsp" title="ÄãºÃÌÖÑá">  About us  </a>
      </td> 
      </center>
      
      <input id="myinput" class="myinput" data-options="vodtype:'telno'">ÊÖ»úºÅÑéÖ¤</input>
      <input id="myinput" class="myinput" data-options="vodtype:'email'">EMAILÑéÖ¤</input>
		  <script type="text/javascript" src="./jquery-1.9.1.js"></script>
		  <script type="text/javascript" src="./input.js"></script>
		  <script type="text/javascript" src="./bootstrap.css"></script> 
		  <script type="text/javascript">
		  	var i = $("#myinput").input({
		  		vodtype:telno
		  	});
		  	
		  	i.input("check");
		  	</script>
	</body>
</html>

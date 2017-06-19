# rating-star 星级评分效果
 
简单 实现代码：
  var rating = (function() {
	    	// 封装函数
	    	function lightOn($item,num) {
	    	    $item.each(function(index) {
	    	        if (index < num) {
	    	            $(this).css({
	    	                "background": "url(../img/star.png) -1px -40px no-repeat"
	    	            });
	    	        } else {
	    	            $(this).css({
	    	                "background": "url(../img/star.png) 0 0 no-repeat"
	    	            });
	    	        }
	    	    })
	    	}
        // 初始化函数
        var init = function(id,num){
        	var $rating = $(id),
            	$item = $rating.find(".rating-item");

           	// var num = 2; //默认两颗星
           	
           	
           	// 初始化
           	lightOn($item,num);
           	// 添加事件
           	$rating.on("mouseover", ".rating-item", function() {
           	    var index = $(this).index();
           	    lightOn($item,index + 1);
           	}).on("click", ".rating-item", function() {
           	    num = $(this).index() + 1;
           	    lightOn($item,num);
           	}).on("mouseout", function() {
           	    lightOn($item,num)
           	})
        }
        // jq插件
        $.fn.extend({
        	rating:function(num){
        		return this.each(function(){
        			init(this,num);
        		})
        	}
        })

        return {
        	init:init
        }

    }) ();

    $("#rating").rating(2);
    $("#rating2").rating(3)
然后在此基础上 又做了进一步扩展

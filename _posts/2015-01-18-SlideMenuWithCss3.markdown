---
layout: post
title:  "SLIDE MENU WITH CSS3"
date:   2015-01-18
tags: instagram
comments: true
---
# **SLIDE MENU WITH CSS3** #

***

## IDEA ##

![idea](http://www.axure.com/c/attachments/forum/6-x-newbie-questions/1122d1349212362-want-menu-slide-out-page-mouseenter-mouse-out-sliding-menu.png)

### **We need 2 css "show", "hide"** ###
![idea1](http://i.imgur.com/47pPZY7.png)

***

## WORK ##

**HTML:**
    
	<div class='slideMenu'>
	<ul>
    	<li><a href="#"> Menu1</a></li>
        <li><a href="#"> Menu2</a></li>
        <li><a href="#"> Menu3</a></li>
        <li><a href="#"> Menu4</a></li>
    </ul>
	</div> 

**CSS**

	.slideMenu.hide {
	  -webkit-transition: 1s;
	  -moz-transition: 1s;
	  -ms-transition: 1s;
	  -o-transition: 1s;
	  transition: 1s;
	  margin-left: -100px; !important;
	}
	.slideMenu.show {
	  -webkit-transition: 1s;
	  -moz-transition: 1s;
	  -ms-transition: 1s;
	  -o-transition: 1s;
	  transition: 1s;
	  margin-left: 0px; !important;
	}

**JQuery**

	$menu = $('.slideMenu');
	$menu.hover(function(){ 
	    $menu.removeClass('hide');
	    $menu.addClass('show');
	},function(){	
		$menu.removeClass('show');
	    $menu.addClass('hide');
	});


<h1>DONE</h1>

##[Demo](http://jsfiddle.net/uLeo2wyf/) ##
---
layout: post
title:  "Dropdown Menu"
date:   2015-01-18
tags: instagram
comments: true
---


# **DROPDOWN MENU** #

***

###

## **IDEA** ##

The menu fade in when **Mouse Enter** and fade out when **Mouse Out**


## **WORK** ##

HTML

	<ul id="menu">
        <li><a href="#" class="dropdown-menu">Menu1</a>
        	  <div class="menu-dropdowned">
                  <ul>
                    <li><a href="">menu 1.1</a></li>
                    <li><a href="">menu 1.2</a></li>
                  </ul>
              </div>
		</li>
        <li><a href="#" class="dropdown-menu">Menu2</a>
        	  <div class="menu-dropdowned">
                  <ul>
                    <li><a href="">menu 2.1</a></li>
                    <li><a href="">menu 2.2</a></li>
                  </ul>
              </div>
		</li>
      </ul>



- We need 2 variable:

	**hadMenuDropdown** : if "true" then menu dropdown is showing, else menu dropdown is hiding

	**menuDropdownHover** : if "true" then mouse enter menu dropdown, else mouse out menu dropdown



- When mouse enter the menu, a menu dropdown will fade in

		if ($hadMenuDropdown =="false")
				{
					$num = $(".dropdown-menu").index(this);
					$temp = $(".menu-dropdowned").eq($num);
					$temp.stop( true, true ).fadeIn(1200);	
					$hadMenuDropdown = "true";
				}	


- When mouse out the menu, a menu dropdown will fade out. To avoid when mouse out the menu, a menu dropdown fade out immediately, we need **setTimeout**

		setTimeout(function(){
				if ($menuDropdownHover == "false")
				{
					$temp = $(".menu-dropdowned").eq($num);
					$temp.stop( true, true ).fadeOut(1200);
					$menuDropdownHover = "false";
					$hadMenuDropdown = "false";
				}
				},1200);

- When mouse enter dropdown menu, we need set $menuDropdownHover = "true" and otherwise $menuDropdownHover = "false"

		 $(".dropdown-menu").mouseenter(function(){
			  	$menuDropdownHover = "true";
		  });
		 $(".dropdown-menu").mouseleave(function(){
			  	$menuDropdownHover = "false";
		  });

- When mouse enter menu dropdowned, we set $menuDropdownHover = "true", and otherwise menu dropdowned fade out.

		$(".menu-dropdowned").hover(function(){
				$menuDropdownHover = "true";
		  }, function(){
			  	setTimeout(function(){
					if ($menuDropdownHover == "false")
					{
						$num = $(".dropdown-menu").index(this);
						$temp = $(".menu-dropdowned").eq($num);
						$temp.stop( true, true ).fadeOut(1200);
						$menuDropdownHover = "false";
					}
				},1200);
		  });

- When mouse enter menu dropdowned, we need set $menuDropdownHover = "true" and otherwise $menuDropdownHover = "false"

		$(".menu-dropdowned").mouseenter(function(){
			  	$menuDropdownHover = "true";
		  });
		  $(".menu-dropdowned").mouseleave(function(){
			  	$menuDropdownHover = "false";
		  });

## DONE ##
###[Demo](http://jsfiddle.net/u50amoav/)###
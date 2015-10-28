## Website Performance Optimization portfolio project

This is a URL of the optimized website http://dinagr.github.io/frontend-nanodegree-mobile-portfolio-master/views/pizza.html

##Optimazations - 

#Pizza.html

1. Dividing the style.css file to a few files and adding media query to some of them.
2. Inline part of the css.

#main.js

1. changePizzaSizes
	1.a. Change the switch - the result will be the new width of the image in precentage
	1.b. Get the 'document.querySelectorAll(".randomPizzaContainer")' out of the loop.

2. Get the creation of pizzaDiv outside of the loop
	for (var i = 2; i < 100; i++) {
  		var pizzasDiv = document.getElementById("randomPizzas");
  	pizzasDiv.appendChild(pizzaElementGenerator(i));
	}

3. updatePositions
	3.a. Get these calculation out of the loop
	var items = document.querySelectorAll('.mover');
  	var scroll = document.body.scrollTop/ 125o0;
  	var numOfPizzas = items.length;
  	3.b. There are 5 results that can be recievd - so they are calculated outside of the main loop
  	var phase = [];
  	for (var j = 0; j < 5; j++){
    	phase[j] = Math.sin(scroll + (j)) * 100;
  	}
  	3.c. Change the transform instead of the left property - this does not activate layout and paint 
  	for (var i = 0; i < numOfPizzas; i++) {
    	/****Calculate where the pizza need to be moved****/
    	var moveX = items[i].basicLeft + phase[i%5];
    	/****The move is being done by transform instead of left - it does not activate the layout and paint****/
    	items[i].style.transform = 'translate3d(' + moveX + 'px, 0,0)';
    	//window.items[i].style.transform = 'translateX(' + ((i % 8) * 256 + (100 * phase[i%5])) + 'px)';
  	}
  	3.d. Adding requestAnimationFrame ofr the activation of this function
  	



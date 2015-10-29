## Website Performance Optimization portfolio project

This is a URL of the optimized website http://dinagr.github.io/frontend-nanodegree-mobile-portfolio-master/views/pizza.html

##Optimazations - 

###index.html / project_2048.jtml / project_mobile.html / project_webpref.html

1. Commenting the fonts that are not working
2. Adding media queries to the css files
3. Inline part of the css
4. Inline one of the js files in the footer and make it async
5. Define all the js as async and move them to the footer

###Pizza.html

1. Dividing the style.css file to a few files and adding media query to some of them.
2. Inline part of the css.

###main.js

1. changePizzaSizes </br>
	1.a. Change the switch - the result will be the new width of the image in precentage </br>
	1.b. Get the 'document.querySelectorAll(".randomPizzaContainer")' out of the loop.

2. Get the creation of pizzaDiv outside of the loop </br>
	for (var i = 2; i < 100; i++) { </br>
  		var pizzasDiv = document.getElementById("randomPizzas"); </br>
  	pizzasDiv.appendChild(pizzaElementGenerator(i)); </br>
	}

3. updatePositions </br>
	3.a. Get these calculation out of the loop </br>
	var items = document.querySelectorAll('.mover'); </br>
  	var scroll = document.body.scrollTop/ 125o0; </br>
  	var numOfPizzas = items.length; </br>
  	3.b. There are 5 results that can be recievd - so they are calculated outside of the main loop </br>
  	var phase = []; </br>
  	for (var j = 0; j < 5; j++){ </br>
    	phase[j] = Math.sin(scroll + (j)) * 100; </br>
  	} </br>
  	3.c. Change the transform instead of the left property - this does not activate layout and paint </br> 
  	for (var i = 0; i < numOfPizzas; i++) { </br>
    	/****Calculate where the pizza need to be moved****/ </br>
    	var moveX = items[i].basicLeft + phase[i%5]; </br>
    	/****The move is being done by transform instead of left - it does not activate the layout and paint****/ </br>
    	items[i].style.transform = 'translate3d(' + moveX + 'px, 0,0)'; </br>
    	//window.items[i].style.transform = 'translateX(' + ((i % 8) * 256 + (100 * phase[i%5])) + 'px)'; </br>
  	} </br>
  	3.d. Adding requestAnimationFrame ofr the activation of this function

4. Creation of the mooving pizza </br>
	4.1. Get lines that can be calculated once out side of the loop. </br>
	4.2. Calculate how many pizzas need to be shown to the user according to the dimensions of the window. </br>
document.addEventListener('DOMContentLoaded', function() { </br>
  /****Calculate this outside of thed loop****/ </br>
  var movingPizzas1 = document.querySelector("#movingPizzas1"); </br>
  var cols = 8; </br>
  var s = 256; </br>
  /****Get the amount of needed pizzas and avoid creating too many pizzas****/ </br>
  var pizzaWidth = Math.floor(window.innerWidth / 73.333); </br>
  var pizzaHeight = Math.floor(window.innerHeight / 100); </br>
  var numOfPizzas = pizzaWidth*pizzaHeight; </br>
  for (var i = 0; i < numOfPizzas; i++) { </br>
    var elem = document.createElement('img'); </br>
    elem.className = 'mover'; </br>
    elem.src = "images/pizza.png"; </br>
    elem.style.height = "100px"; </br>
    elem.style.width = "73.333px"; </br>
    elem.basicLeft = (i % cols) * s; </br>
    elem.style.top = (Math.floor(i / cols) * s) + 'px'; </br>
    console.log(elem.style.top); </br>
    movingPizzas1.appendChild(elem); </br>
  } </br>
  updatePositions(); </br>
});

#### Images 

minimizing the images in free websites

### minimze the css files and part of the js files 

The html files and the main.js file were not minimizes so the reviewer will be able to check them.
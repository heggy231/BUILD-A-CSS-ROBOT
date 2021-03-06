Part 1: Customize shapes using CSS border properties
  Need: robots with laser eyes, be his best friend.
  - Mission: 
  1) Making simple shapes with HTML and CSS
  2) Sneaky ways to use border properties
  3) New tricks with gradients and background-size

  1) Shapes and Flow:
  <div> element as a container; sometimes it held images, sometimes text, sometimes both!
  
  Looking at <div> on itw own!

- Like everything else, div - invisible rectangles.
  * How to make <div> visible, three things need to happen: To make div seen with no content: width, height, and color!
  1) width, 
  2) height, 
  3) background or border color

  div {
    height: 150px;
    width: 300px;
    background: #cc5;
  }

- this div will be robot! using HTML and CSS!
  * Why are we building robot with HTML and CSS?  
    If I can position multiple HTML elements to build a robot in CSS (some JS), I can lay out all kinds of other things!  No website layout will be too complex!  No oddly-angled or multicornered textbox will elude your shape-making and getting-things-to stay-where-you-want-them-on-the-page skills!

- starting point: stack 3 divs
<div class="brain"></div>
<div class="torso"></div>
<div class="foot"></div>
  * Note: normal flow of the web, everything on web page likes to stack flush on top of each other.

- All three divs look the same.  Make each div unique!
1) foot! create a circle!
  .foot {
    height: 40px;
    width: 40px;
    background: #ccc;
  }

  - we have box, let's make it circle use border radius!  border-radius create circle, ovals, eggs anything with some curve to it!
  remember this?
  div {
    margin: top right bottom left;
  }
  Similar to margin, border-radius declaration
  div {
    border-radius: topleft topright bottomright bottomleft
  }

  - When you wanted all four sides of an element to have the same padding or margin, you only had to declare that pixel value once.  Same for border-radius when all 4 radii have same value.
  if you give all same radii > it is circle!

  - To make circular curve, radius be at least half the length of the shape's edge.  since foot length is 40px, you only need 20px for border-radius. (just the half the size length.  anything less than 20px will look squarish rather than round!)
   border-radius: 20px;

  - put border in foot circle: border needs 3 attribute to become visible.

    div { border: width style color; }
    
    declare width in px, color any value system
    border style: solid, dashed, dotted, double

    adding border will increase the width of the foot box.  therefore, increase the border-radius to accommodate the increase in length.  

    .foot {
      border-radius: 40px;
      border: 15px solid #999;
    }

  - Style the borders of any HTML element one by one to make triangles, stars, trapezoids, and more:
    div {
      border-left: width style color;
      botder-top: width style color;
      etc...
    }
  ex) of css for .triangle (div has no width, no height, no background color, so it shouldn't be visible.  There is width, style, and color for bottom border)
    .triangle {
      height: 0;
      width: 0;
      border-left: 50px solid transparent;
      border-right: 50px solid transparent;
      border-bottom: 100px solid red;
    }
  Note: You are not seeing any div but just bottom border with left and right cutting into it (since it is transparent!)

  - Trapezoid shape of Robot's torso: it is exactly like triangle except it has width value.
    .torso {
      height: 0;
      width: 140px;
      border-top: 300px solid #bc6;
      border-left: 75px solid transparent;
      border-right: 75px solid transparent;
    }
- Get rid of background color of div
    background: #ccc removed!
  Note: everything is positioned normal document flow: flush left, stacked tightly on top of each other.
    1) center the div!
      margin: 0 auto;
    2) curve the edge of torso
      border-radius: 20px 20px 100px 100px;

- Brain!  
  1) Made head visible by giving it color, height, and width
  .brain { 
    background: #cc5;
    height: 150px;
    width: 150px;
    }

  2) add round head border-radius!
    border-radius: 60px 60px 10px 10px;
    border-bottom: 40px solid #666;
    // border-bottom only one side of the shape a contrasting border.

    - different look for robot head
    border-radius: 60px 60px 10px 10px;
    border-bottom: 40px double #666;

    border-radius: 60px 60px 0 0;
    border-bottom: 40px dotted #666;

- Laser beam eyes!  use radial gradient:
Radial gradients radiate outward, in all directions, from a central point.
  div {
    background: radial-gradient(shape, centercolor, outercolor);
  }
  For gradient's shape: circle or ellipse 
  For color: numerical callout to size (in pixels or in percent)

  .brain {
    background: radial-gradient(circle, white 15%, transparent 40%), #cc5;
  }
  // add in radial gradient with preserve the existing background color!
  * by default a round gradient wants to be centered in HTML element that contains it.  Use this default and use background-size, to control how many times, and where, it appears in the shape.

  - By default, gradient wants to be centered in the background.
    Use this default characteristic and background-size to trick it into thinking background isn't 150x150 px.  We want 2 gradients, so we'll make it half that size!
brain {
  background-size: 75px; // half of 150 width makes 2 eyes!
}

Why would cutting the background-size in half give it four eyes?  
  B/c it thinks there are four 75x75 px background to fill!
brain {
  background-size: calc(75px/2) calc(150px/2);
}

We actually want the gradient to think it's only half of width, but still the full 150px height.

background-size: width height;
background-size: 75px 150px;

OR use % for skipping Math
background-size: 50% 100%;

- If you make transparent 0 - glow goes away
background: -webkit-radial-gradient(circle, white 36%, transparent 0%), #cc5;

- Robot to take orders, give it an antenna!
.beep class right above brain div
.beep {

}
<div class="beep"></div> //antenna
  Note: robot bumped down beep div is pushing down 150px height!

- flesh out basics of antenna's size, style, color
  * look 80px tall
    notice it is not the height of div but the thickness of the border
.beep {
  width: 5px;
  height: 0;
  /* border: width style color */
  border-bottom: 80px solid #888;
}

- Adding transparent left and right border will give the antenna a trapezoid shape like the torso.  But when we add a top border, something awesome!
  * since border-right and border-left need the same CSS, take advantage of the cascade and assign that style to all borders!
  * Then override border-top and border-bottom!

  .beep {
    width: 5px;
    height: 0;
    /* border: width style color */
    border: 5px solid transparent;
    border-top: 10px solid #777;
    border-bottom: 80px solid #888;
  }

# Part 2: Using CSS to position elements on a webpage
Make robot disco with me, shoot lasers
- Mission:
1. CSS positioning in depth
2. The idea of "in front of" and "behind" in CSS
3. Writing CSS transforms to flip and rotate elements

1. CSS positioning in depth
  - Get on grid sytem.  
    We have been dependent on margin to line up all piece of robot.  once we take off margin.. nothing lines up!
    We used margin-zero-auto to build robpt parts b/c learning borders and radial is hard enough.  
    - now, focus on CSS Positioning, since we want the robot to free to move around the screen!  It can't glued to the middle of the page.

- got rid of all the styling for div use CSS positioning
  div {
    height: 150px;
    width: 300px;
    margin: 0 auto;
  }
  * x,y,z coordinates: z as third dimension
    - As you move right x-val increases
    - move down, y-val increases
    - Unit used for grid squares = pixels
  
  * 5 ways to position top right bottom left z-index things:
    1st) static: default positioning
    2nd) relative: move relative to others
    - any time not static, you escape from normal flow and opens door to call on four new properties: top, right, bottom, left
    3rd) left, top: X, Y Axes  (you can use them to declare from left side, from top of, its container in px)

    - We are not using right, bottom, b/c we want everything oriented same direction.

    - when .beep is relatively positioned, "go 70px away from the left side!"
    .beep {
      /* kick off free positioning */
      position: relative;
      /* go away 70px from left or move 70px to right */
      left: 70px;
    }

    Note: how much left you can go?  just trial and error!

    - Let's move the head!  Remember to move the antenna along with it!
    * Assign the .brain style position of relative
    * Give .brain left: 70px
    * Increase .beep left: 140px
    .brain {
      position: relative;
      left: 70px;
    }
    .beep {
      left: 140px; // beep once was 70px but brain moved 70px therefore add 70px more!
    }
    - Move the wheels .foot relation to the robot .torso:
    .foot {
      position: relative;
      left: 110px;
      top: -10px;
    }

    Why assign negative value to top for .foot?
      - a negative top value moves things up, twd the top of the page, by the specified number of pixels.  
      A negative left value will move things to the left!  relative to .torso    

- Z axis: 
z by default if zero.  Deeper into page, -z
closer to the viewr +z. If you want thing go infront give it a > 1 z-value.  Behind < 1 z-value.
Like top, left, etc, z-index only works on positioned elements.

.foot {
  z-index: -1;
}

- Summary of what we did: Cotbot is positioned in relation to one another, rather than being dependent on the center of the screen.

- Question to Francisco:

http://jsbin.com/kutigefeso/1/edit?html,css,output

When I say .foot {
position: relative;
top: -10px
}

- How does browser know that top is suppose to be positioned relative to .torso?

- Let's move the robot around the screen!  Let's stick all robot parts!  <style> cascade down from the outermost containers to the inner ones. 

So create outer HTML element that contains all the robot pieces.  If we wrote CSS style for that container element, those style should effect every HTML element inside the container.

  - Create new div class called: "robot", wrap it around the four other divs that robot pieces.
  * before
  <div class="beep"></div>
  <div class="brain"></div>
  <div class="torso"></div>
  <div class="foot"></div>

  * after (wrap all the pieces inside). .robot is container element that contains all four HTML element.
  <div class="robot">
    <div class="beep"></div>
    <div class="brain"></div>
    <div class="torso"></div>
    <div class="foot"></div>
  </div>

- any CSS style should be inside .robot container-div
  * Q&A: Everything on pg is already inside of <body>!  Why am putting it inside of body container?
  * Answer: Normally, yes, we can use body as container.  what if we want to move the robot in and out of the body as one contained object.
 
    // position will move entire Cotbot over to right!
    .robot {
      position: relative;
      left: 200px;
    }

  http://jsbin.com/kozapa/5/edit?html,output

  - Arm the robot: build cobot with arms and CSS shapes! arm could be letter J in google web font!

  Use Poller One: https://fonts.google.com/specimen/Poller+One

    - click + sign and use embed font link, CSS style
    <link href="https://fonts.googleapis.com/css?family=Poller+One" rel="stylesheet">

    font-family: 'Poller One', cursive;

    - Now we have access to google web font poller one:
    1) add j to the page
    2) use css to make it right size and font.
      Nest dive for the left and right arm inside the torso <div>.  This tells the arms to obey anything we tell the torso, will save lot of hassle later on!
        <div class="torso">
          <div class="left">j</div>
          <div class="right">j</div>
        </div>
        
  .left {
    font-family: 'Poller One', Verdana, arial, sans-serif;
    font-weight: bold;
    font-size: 250px;
    color: #666;
  }
    - For left arm rotate about half turn. next, come up to top of the torso div.  Also, tuck it behind the robot's shoulder.  
      transform: will help with angle of the arm rotated.

        .left {
          transform: rotate(200deg);
          -webkit-transform: rotate(200deg);
          -moz-transform: rotate(200deg);
        }
      1. Apply relative positioning to left arm
        position: relative;
      2. Give .left left: -190px;
      3. Give .left top: -320px;
  - Now for Right arm!
  .right {
    font-family: 'Poller One', Verdana, arial, sans-serif;
    font-weight: bold;
    font-size: 250px;
    color: #666;
  }
.right {
  transform: rotate(184deg); // anyway you transform the arm it still looks like left arm
}

  - to correct this: use scaleY, finds the center of the element, flips it along the Y-axis.
    * Problem! You can only declare transform once for any item you style.  But we need transform: rotate, transform: scaleY 

// if something needs more than one transform, they all get listed together in the same declaration
.right {
  transform: scaleY(-1) rotate(20deg);
  -webkit-transform: scaleY(-1) rotate(20deg);
  -moz-transform: scaleY(-1) rotate(20deg);
}

- Now, right arm is oriented right way.  Let's move it up!
  1) to take it out of regular document flow. position: relative.
  2) right: -203px; top: -612px; z-index: -1;

- Laser beam eyes! use CSS animation
  1) define CSS anima
    - define based on the property you want to change of the element you're animating
      We are animating .brain, we want to change the color of the eye gradient, which is part of background property!.  We want animation to flash from white to red. Keyframing is an animation term (animators only worked on the most important frames, and the in-between frames were drawn by assistants.)
      We are making a keyframe animation called blink.  


      * before 
      .brain {
        background: radial-gradient(circle, white 15%, transparent 40%), #cc5; 
      }
  http://jsbin.com/kozapa/12/edit?html,output

      * after
      // make a keyframe animation: blink
      @keyframes blink {
        50% {
          background: radial-gradient(circle, red 15%, transparent 40%), #cc5;
        }  
      }
      
      // At the start and end of the animation, it will be the same as .brain's default background, with white eyes.
      // 50% of the way through the animation, the color changes from white to red.  @keyframes 50% { ... red ...}
      // Only element is changing once, only need single keyframe.
      // order matters: 1) Define keyfram above the .brain. 
      // 2) Assign it to brain; animation: blink, make it .5seconds long and repeat it infinity.

      .brain {
        animation: blink .5s infinite;
      }

    http://jsbin.com/kozapa/14/edit?html,output

  2) Assign CSS anima
  Remember the vendor prefix!
  
  @-webkit-keyframes blink {
    50% {
      background: -webkit-radial-gradient(circle, red 15%, transparent 40%), #cc5;
    }  
  }
  @-moz-keyframes blink {
    50% {
      background: -moz-radial-gradient(circle, red 15%, transparent 40%), #cc5;
    }  
  }

  http://jsbin.com/kozapa/15/edit?html,output

3) more on vendor prefix,  
.brain {
    animation: blink .5s infinite;
    -webkit-animation: blink .5s infinite;
    -moz-animation: blink .5s infinite;

- How to get the blink to stop?
1. comment out laser eye keyframe definition
- control the lazer eye

http://jsbin.com/zupivi/edit?html,css,output


# Part 3: Creating and Controlling Animations with JS.
- Mission:
1. Build a Button to control the robot's laser eyes
2. Write JavaScript Program that generates random colors to help Cotter dance all night!


1. Build a Button to control the robot's laser eyes
  On/Off Button: 
    1) CSS class applying more than one html element
    2) HTML <button> tag
    3) JQuery toggleClass function

  1) Create special class for when eyes should be blinking, separate from the regular .brain style.
    - Call it .laser! Take out .brain's CSS animation out and put inside of .laser
    // animation css from .brain is now inside .laser!
    .laser {
      animation: blink .5s infinite;
      -webkit-animation: blink .5s infinite;
      -moz-animation: blink .5s infinite;
    }

  * This will now stop it from blinking since no HTML element is assigned to .laser class yet!
   http://jsbin.com/kozapa/21/edit?html,output

   <!DOCTYPE html>
<html>
<head>
<meta name="description" content="dash GA make a robot project">
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>COTBOTS</title>
  <link href="https://fonts.googleapis.com/css?family=Poller+One" rel="stylesheet">
  <style>
/* position relative; take robot out of normal doc 
    flow and move Cotbot over to right! 
    .robot is container for all of its 
    robotie parts 
*/
  .robot {
      position: relative;
      left: 200px;
  }
  .beep {
    width: 5px;
    height: 0;
    /* border: width style color */
    border: 5px solid transparent;
    border-top: 10px solid #777;
    border-bottom: 80px solid #888;
    /* opens .beep to break out of static positioning */
    position: relative;
    /* go away from left side means push 70px to right */
    left: 140px;
  }
  @keyframes blink {
    50% {
      background: radial-gradient(circle, red 15%, transparent 40%), #673AB7;
      /* half of 150 width makes 2 eyes! */
      background-size: 50% 100%;
    }  
  }
  @-webkit-keyframes blink {
    50% {
      background: -webkit-radial-gradient(circle, red 15%, transparent 40%), #673AB7;
      background-size: 50% 100%;
    }  
  }
  @-moz-keyframes blink {
    50% {
      background: -moz-radial-gradient(circle, red 15%, transparent 40%), #673AB7;
      background-size: 50% 100%;
    }  
  }
  .laser {
    animation: blink .5s infinite;
    -webkit-animation: blink .5s infinite;
    -moz-animation: blink .5s infinite;
  }
  .brain { 
    background: radial-gradient(circle, white 15%, transparent 40%), #673AB7;
    background: -webkit-radial-gradient(circle, white 15%, transparent 40%), #673AB7;
    background: -moz-radial-gradient(circle, white 15%, transparent 40%), #673AB7;
    /* half of 150 width makes 2 eyes! */
    background-size: 50% 100%;
    height: 150px;
    width: 150px;
    border-radius: 60px 60px 10px 10px;
    border-bottom: 40px double #666;
    position: relative;
    left: 70px;
  }

  - Next, toggle .laser on|off, just like .show-description class in Esha's Restaurant.
    1) Make toggle on|button for .laser. after robot div in HTML.
      </div> // robot div closing
      <button> laser eyes on|off <button>
      </body>
    2) name button to class flash
      <button class="flash"> laser eyes on|off <button>
      flash functions as toggle (turn something on/off)
    3) add jQuery
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

      or using GA Jquery
      <script src="/assets/jquery.js"></script>

    4) jQuery lib has a function commonly used such as toggleClass!  "JQuery: when you hear a click on the .flash class, toggle the class .laser on .brain!"
<script>
    $('.flash').click(function() {
      $('.brain').toggleClass('laser');
    });

    // insert this code end of the body!
</script>
    http://jsbin.com/kozapa/24/edit?html,output


"From a design perspective, the syntax for jQuery is: "When I do this, make the CSS do this."

The more common slogan is: Find something, do Something."

- Chris Coyler

"JQuery: when you hear a click on the .flash class, toggle the class .laser on .brain!"
<script>
    $('.flash').click(function() {
      $('.brain').toggleClass('laser');
    });

    // insert this code end of the body!
</script>
https://dash.generalassemb.ly/projects/cotbots-3

// when JQuery hears click on class .flash
$('.flash').click();

... it should add (or remove) the .laser class to (or from) anything with a .brain class.
function() {
  $('brain').toggleClass('laser');
}

- Next, background color change for coBot robot flashing strobe light color.  Instead of writing alternate body style and toggling it on|off, you're going to generate an infinite number of random colors!!!

  * What your code will do:
  1) Listen to button clicked
  2) Generate random color value background
  3) Change <body> background to new color

  1. Make a button by with class="color"
  2. Generate a completely random color value.  Use Math. function.
    - WE used functions that do useful things, like .click and .toggleClass.

    - work with functions that p
    Produces value! a number
      RGBA(red, green, blue, alpha)
      value 0 - 255

      000         black
      255 255 0   yellow
      255 255 255 white

      Create a random numbers (0 to 255), then assigning 1 as the alpha value, 

rgba(random, random, random, 1)
ex) rgba(253, 88, 48, 1)  // red
    rgba(38, 107, 204, 1) // blue

Math.floor(Math.random() * 255) // 0 - 255
Math.floor(Math.random() * 3) // 0 - 3
  This gives the number between what ever number you multiply and zero!

// when color is clicked, pick a number 0-255
$(".color").click(function() {
  var number = Math.floor(Math.random() * 255);

  // display the number in an alert window
  alert(number);
});
http://jsbin.com/kozapa/27/edit?html,output

- Math.random() method creates random number betwn 0 an 1.
  0 X 255 = 0
  1 X 255 = 255
  // Mult random number by 255, get random number btwn 0 and 255.

- Math.floor() rounds any value down!! to a whole number
  0.5 x 255 = 127.5
  Math.floor(127.5) = 127

  0.831 x 255 = 211.905

  Math.floor(211.905) = 211 // only takes the integer part of the number

- Next, Make JS remember those numbers by storing it!  Grad number btwn 0 - 255!  only the integers (Math.floor)
var red = Math.floor(Math.random() * 255);

  -How to get one function to create mult. variables?  RGB color values

  $(".color").click(function() {
    var red = Math.floor(Math.random() * 255);
    var green = Math.floor(Math.random() * 255);
    var blue = Math.floor(Math.random() * 255);
  });

  * summary: when .color is clicked, generate red 0 - 255, green 0 - 255, blue 0 - 255
  // when color clicked
  $(".color").click(function() {
    var red = Math.floor(Math.random() * 255);
    var green = Math.floor(Math.random() * 255);
    var blue = Math.floor(Math.random() * 255);

    // display the three values in an alert window
    // rgb(38, 107, 204) - red green blue
    alert(red + "," + green + "," + blue);
  });

# Part 4: Make and Modify CSS Styles with JavaScript
  1. Convert your random numbers into brand-new CSS
  2. Help the robot make some groovy mood lighting
  3. Give Cotter the chance to go out dancing with his robot

  1) Variable Recap: 
    - have names
    - greedily slurp up values
    - split values out where you tell them

  This combines 3 var you already made into a brand-new var called 

  var randomRGBA = 'rgba('+red+', '+green+', '+blue+', 1)';

-- update on code ---
  $(".color").click(function() {
    var red = Math.floor(Math.random() * 255);
    var green = Math.floor(Math.random() * 255);
    var blue = Math.floor(Math.random() * 255);
    var randomRGBA = 'rgba('+red+', '+green+', '+blue+', 1)';

    alert(randomRGBA);
  });

  * randomRGBA is the RGBA value that will put into your CSS to change the screen's background color!

http://jsbin.com/kozapa/30/edit?html,output

- String Theory:
  JavaScript treats '' quotes as a special type of value called a string, which is treated as regular text, not as code.  

  - comment out 
  alert(randomRGBA);

  - Get JS to do something with randomly generated RGBA value byt applying into CSS background!

We want to insert something like this into CSS!
Use JQuery
    body {
      background: rgba(red, green, blue, 1);
    }

- Making CSS with JS: JQuery function toggleClass Add CSS classes to your existing HTML, and to take them out.  

// Tells JS to change the body's background to your randomRGBA value in the css.

  // change the body's background to random color
  $("body").css("background", randomRGBA);

- http://jsbin.com/kozapa/31/edit?html,output

- Make Patrick dance gif robot!
where gif lives:
http://dash.ga.co/assets/dance_cotter.gif

<img src="http://dash.ga.co/assets/dance_cotter.gif">

position Patrick next to robot
  img {
    position: absolute;
    top: 200px;
    left: 400px;
  }

http://jsbin.com/kozapa/32/edit?html,output

- Use @keyframe animation to make the robot's eyes blink.  It affected the background prop of the brain class.

  - keyframe anima will affect the position of the img!
  - img will start from 800px away from the left side of the screen and then move to its defined left position of 400px.

// img start 800px away from left
@keyframes dance {
  from {
    left: 800px;
  }
}
// add -webkit-
@-webkit-keyframes dance {
@-moz-keyframes dance {

// defined patrick's position
img {
    position: absolute;
    top: 200px;
    left: 400px;
}

- It takes two to work for keyframes! Nothing happens b/c img doesn't know that it's supposed to listen to dance yet!
// part 1, define keyframes
@keyframes dance {
  from {
    left: 800px;
  }
}
// run img style animation script for 4 sec
img {
  animation: dance 4s infinite;
  -webkit-animation: dance 4s infinite;
  -moz-animation: dance 4s infinite;
}

http://jsbin.com/kozapa/32/edit?html,output

- Add a button to stop Patrick from dancing
<button class="moves">break/dance</button>
http://jsbin.com/kozapa/34/edit?html,output

- Toggle vs. ToggleClass
No need to toggle a class on img element; can toggle the element itself.

  * JQuery click the moves button, every imag on the page will toggle on or off.
    $(".moves").click(function() {
      $("img").toggle();
    });
Use toggleclass to add or subtract a class from HTML element.  If you toggle an HTML element itself, all instances of that element will be added or subtracted from the page!  Warning!  for our site we only have 1 img!

// "JQuery: when you hear a click on the .flash class, toggle the class .laser on .brain!"
  $('.flash').click(function() {
    $('.brain').toggleClass('laser');
  });

// toggle img patrick dancing on or off when click on moves button
  $(".moves").click(function() {
    $("img").toggle();
  });
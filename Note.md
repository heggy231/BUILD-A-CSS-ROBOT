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
  
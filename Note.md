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
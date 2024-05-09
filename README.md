# raskell
Graphics Generator with Haskell and OpenGL
This program is a graphics generator written in Haskell using OpenGL(cross-platform API for
rendering 2D and 3D graphics) and GLUT (Windows system independent toolkit for
writing OpenGL programs).
It will give you the ability to draw points, lines, basic shapes, and fractals. This project is a great
starting point for learning OpenGL, understanding package management in Haskell, and
showing off your Haskell wizard magic (types, lexing, parsing, recursion).
User Interface:
When you run the raskell file, you will be given the following options. Each option allows you to
run/test our code (except for Back and Quit).
1. Load
Enter the name of a poly file (with extension) to draw the shapes
outlined in the file (one per line). This is also the only way to generate
multiple shapes at once.
2. New
Choose something to draw (each option then asks for corresponding
inputs):
1. Point
2. Line
3. Triangle
4. Rectangle
5. Circle
6. Fractal
7. Back (to the first menu)
3. Quit
Let's dive into how to get started with our project.
To Run the program:
1) Run our cute little .exe. Only works on windows devices.
To package your own GLUT/OpenGL haskell exe!
1) Download GHCup to install ghci and cabal-install packages.
2) Use cabal init wherever you want your project to initialize a cabal environment
3) Update your .cabal file to reflect all the libraries you need for the project. (here just GLUT
and GHCI)
4) Download freeglut
5) Move the DLL into a folder inside the project. Copy the abostule path to the freeglut DLL
and add it to your PATH. Cabal should now automatically bind the DLL to the .exe,
allowing you to run OpenGL and GLUT in haskell!
6) Now just import the packages in the haskell script and run cabal run. (cabal build and
cabal list are very useful for debugging this process.)
2. Organization
The program is organized into several parts:
Lexer: Converts input strings into tokens.
Parser: Converts tokens into shapes.
Drawing Functions: Functions to draw different shapes using OpenGL.
Main Function: Initializes OpenGL, parses input, and displays shapes.
IO Handlers: Handle different options in the IO, one for each shape.
.poly Files: Syntactically defines shapes datatypes for use in the .exe.
Key functions include:
lexer: Tokenizes input strings.
parser: Parses tokens into shapes.
draw: Renders shapes on the OpenGL window.
displayCanvas: Callback function for displaying the OpenGL window.
drawRectangleFractal and drawTriangleFractal: Recursive functions to draw fractals.
Syntax for .poly files:
All shapes (except points) are defined within square brackets such that it appears as
[<parameters>]. This is how we were able to determine the start and end of shape declarations.
Each shape has its own unique pattern of declaration which ensures no confusion in the parsing
process. The only real constraint is in how numbers must be represented as floats in the syntax
(i.e 0 = 0.0 etc.). Shapes can be defined as follows:
Point: (<x value>, <y value>)
Line: [<point> <point>]
Triangle: [<point> <point> <point>]
Rectangle: [<length> <width> <point (origin)>]
Circle: [<radius> <point (origin)>]
Fractal: [<shape> <number of iterations>]
Examples in order:
(1.5, 0.5)
[(1.5, 0.5) (0.5, 1.5)]
[(0.5, 0.5) (0.25, 1.0) (1.0, 0.5)]
[1.0 1.0 (1.5, 0.5)]
[1.0 (1.5, 0.5)]
[[1.0 1.0 (1.5, 0.5)] 11.0]
3. Research Findings
I think the best way to show off what kind of resources we pulled would be to backtrack
what methods needed help in creation. We specifically had issues with drawing a circle as a list
of points, and also figuring out how to make our idea come to life. We wanted to use openGL
and Glut, and we also wanted to show off our parsing skills. We could have used the premade
libraries for drawing shapes given by openGL, but that would have been too easy. For example,
we could draw a rectangle as a RenderPrimative of lines, but instead we chose to render
everything as a collection of points. This is so we can use our own custom data types for token
handling and parsing in the final product. This challenging approach to rendering was at first
overwhelming, but after a few shapes it was fun! Finding the shape's constraints from our basic
understanding of geometry was almost easy. Until. The circle.
It took Us A total of an hour or two to complete the basic triangle, point, line, and
rectangle. To create a circle, It took us closer to 3-4 hours. It was easier to make the complex
compositions like the fractals, then to make a circle. We ended up using this guide to
understand exactly how you can find a single point on a circle. Then, Using a list
comprehension and some clever trigonometry, we were able to generate a list of points, with
NumPoints, and Radius.
Another very difficult part of our research was just creating a line given two points. It was
only really difficult to get started with it, but after looking at Haskell's OpenGL documentation, I
had found the proper way to render a line as a list of points.

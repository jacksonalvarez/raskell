# Graphics Generator with Haskell and OpenGL

This program is a graphics generator written in Haskell using OpenGL (a cross-platform API for rendering 2D and 3D graphics) and GLUT (a Windows system-independent toolkit for writing OpenGL programs). It provides the ability to draw points, lines, basic shapes, and fractals. This project is an excellent starting point for learning OpenGL, understanding package management in Haskell, and showcasing Haskell wizardry with types, lexing, parsing, and recursion.

## User Interface

Upon running the Haskell file, the user is presented with the following options:

1. **Load**: Enter the name of a `.poly` file (with extension) to draw the shapes outlined in the file.
2. **New**: Choose a shape to draw, with options for point, line, triangle, rectangle, circle, or fractal.
3. **Quit**: Exit the program.

## Getting Started

### Running the Program

To run the program:

1. Execute the `.exe` file. Note: This works only on Windows devices.

### Packaging Your Own GLUT/OpenGL Haskell Executable

To package your own GLUT/OpenGL Haskell executable:

1. Download GHCup to install `ghci` and `cabal-install` packages.
2. Use `cabal init` to initialize a cabal environment for your project.
3. Update your `.cabal` file to include the necessary libraries (here, GLUT and GHCi).
4. Download FreeGLUT.
5. Move the FreeGLUT DLL into a folder inside your project and add its absolute path to your `PATH` environment variable.
6. Import the necessary packages in your Haskell script and run `cabal run` to build and run your executable. (`cabal build` and `cabal list` are useful for debugging.)

## Organization

The program is organized into several parts:

- **Lexer**: Converts input strings into tokens.
- **Parser**: Converts tokens into shapes.
- **Drawing Functions**: Functions to draw different shapes using OpenGL.
- **Main Function**: Initializes OpenGL, parses input, and displays shapes.
- **IO Handlers**: Handle different options in the IO, one for each shape.
- **.poly Files**: Define shapes syntactically for use in the `.exe`.

### Key Functions

- **lexer**: Tokenizes input strings.
- **parser**: Parses tokens into shapes.
- **draw**: Renders shapes on the OpenGL window.
- **displayCanvas**: Callback function for displaying the OpenGL window.
- **drawRectangleFractal** and **drawTriangleFractal**: Recursive functions to draw fractals.

## Syntax for .poly Files

Shapes in `.poly` files are defined within square brackets `[...]`. Each shape has a unique declaration pattern. Numbers must be represented as floats. Shapes can be defined as follows:

- **Point**: `(<x value>, <y value>)`
- **Line**: `[<point> <point>]`
- **Triangle**: `[<point> <point> <point>]`
- **Rectangle**: `[<length> <width> <point (origin)>]`
- **Circle**: `[<radius> <point (origin)>]`
- **Fractal**: `[<shape> <number of iterations>]`

## Research Findings

The development process involved challenges in drawing shapes using OpenGL and GLUT while showcasing parsing skills. Some specific findings and challenges include:

- Drawing a circle was particularly challenging, requiring understanding of trigonometry to generate a list of points.
- Creating a line given two points required understanding the proper rendering method in Haskell's OpenGL documentation.
- Rendering shapes as collections of points instead of using premade libraries provided by OpenGL added complexity but allowed for custom token handling and parsing.

The development process involved overcoming these challenges, resulting in a functional graphics generator that demonstrates various Haskell skills.

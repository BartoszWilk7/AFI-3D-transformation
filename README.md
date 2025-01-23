# Project Title: Laboratory GK - AFI

## Overview
This project demonstrates the implementation of a 3D interactive scene using OpenGL and GLUT. It includes animated objects such as a cube, torus, and teapot, with transformations and rotations applied to showcase fundamental graphics programming concepts.

## Features
- **Interactive 3D Scene**: Real-time rendering of 3D objects.
- **Object Animations**: Dynamic transformations (translation, rotation, scaling) for cube, torus, and teapot.
- **Lighting and Materials**: Basic lighting and material properties for realistic effects.
- **Camera Manipulation**: Custom camera manipulation using `zprInit`.

## Project Structure
```plaintext
project/
├── main.cpp          # Main source file containing the implementation
├── zpr.h             # Header file for camera manipulator
├── README.md         # Project documentation
```

## Prerequisites
Make sure you have the following installed:
- **C++ Compiler**: GCC or any compatible compiler.
- **OpenGL Libraries**: `GL`, `GLUT`, and `osg`.
- **Build Tools**: Make or an IDE like Visual Studio, Code::Blocks, or CLion.

## Setup and Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```

2. Navigate to the project directory:
   ```bash
   cd project
   ```

3. Compile the code:
   ```bash
   g++ main.cpp -o labGK -lGL -lGLU -lglut -losg
   ```

4. Run the executable:
   ```bash
   ./labGK
   ```

## Implementation Details

### Code Highlights
#### Object Initialization
```cpp
void initObjects() {
    cubeMatrix *= osg::Matrix::translate(1, 0, 0);
    torusMatrix *= osg::Matrix::translate(1, -1, 0);
    teapotMatrix *= osg::Matrix::translate(0.5, -0.5, 0);
}
```
Initializes the positions of the cube, torus, and teapot.

#### Cube Animation
```cpp
void updateCube() {
    long inteval = 100;
    auto tmp = cubeMatrix.getTrans();
    static int sign = 1;
    float c = 0.01f;

    if (t % inteval == 0) {
        sign *= -1;
    }
    cubeMatrix *= osg::Matrix::translate(-tmp);
    cubeMatrix *= osg::Matrix::scale(1 + sign * c, 1 + sign * c, 1 + sign * c);
    cubeMatrix *= osg::Matrix::translate(tmp);
}
```
Applies scaling animation to the cube.

### Lighting and Material
```cpp
const GLfloat light_ambient[] = { 0.0f, 0.0f, 0.0f, 1.0f };
const GLfloat light_diffuse[] = { 1.0f, 1.0f, 1.0f, 1.0f };
const GLfloat light_specular[] = { 1.0f, 1.0f, 1.0f, 1.0f };
const GLfloat light_position[] = { 2.0f, 5.0f, 5.0f, 0.0f };

const GLfloat mat_ambient[] = { 0.7f, 0.7f, 0.7f, 1.0f };
const GLfloat mat_diffuse[] = { 0.8f, 0.8f, 0.8f, 1.0f };
const GLfloat mat_specular[] = { 1.0f, 1.0f, 1.0f, 1.0f };
const GLfloat high_shininess[] = { 100.0f };
```
Configures lighting and material properties for rendering.

### Camera Manipulation
```cpp
zprInit();
```
Initializes the camera manipulator for interactive control.

## Usage
- Run the program to view the animated 3D scene.
- Use the mouse and keyboard (if implemented in `zpr.h`) to manipulate the camera.

## Known Issues
- None reported.

## Future Improvements
- Add user interaction for modifying object properties.
- Implement additional animations and effects.
- Improve code modularity by separating classes for objects and their transformations.

## Author
**Bartosz Wilk**

## License
This project is for academic purposes and is not licensed for commercial use. Contact the author for permissions or inquiries.

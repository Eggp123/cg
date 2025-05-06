#include <GL/glut.h>
#include <iostream>
using namespace std;

int radius;

// Plot 8 symmetric points for the circle
void plotCirclePoints(int x, int y) {
    glBegin(GL_POINTS);
        glVertex2i( x,  y);
        glVertex2i(-x,  y);
        glVertex2i( x, -y);
        glVertex2i(-x, -y);
        glVertex2i( y,  x);
        glVertex2i(-y,  x);
        glVertex2i( y, -x);
        glVertex2i(-y, -x);
    glEnd();
}

// Bresenham circle drawing
void drawCircle(int r) {
    int x = 0, y = r;
    int d = 3 - 2 * r;

    while (x <= y) {
        plotCirclePoints(x, y);
        if (d < 0)
            d += 4 * x + 6;
        else {
            d += 4 * (x - y) + 10;
            y--;
        }
        x++;
    }
}

// Draw X and Y axes
void drawAxes() {
    glColor3f(1.0, 0.0, 0.0);  // Red color for axes
    glBegin(GL_LINES);
        glVertex2i(-300, 0); glVertex2i(300, 0);  // X-axis
        glVertex2i(0, -300); glVertex2i(0, 300);  // Y-axis
    glEnd();
}

// Display everything
void display() {
    glClear(GL_COLOR_BUFFER_BIT);

    drawAxes();                // Draw X and Y axes
    glColor3f(1.0, 1.0, 0.0);  // Yellow color for circle
    drawCircle(radius);        // Draw circle at center

    glFlush();
}

// Initialize OpenGL
void init() {
    glClearColor(0.0, 0.0, 0.0, 0.0);  // Black background
    gluOrtho2D(-300, 300, -300, 300);  // World coordinates
}

// Main function
int main(int argc, char** argv) {
    cout << "Enter the radius of the circle: ";
    cin >> radius;

    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
    glutInitWindowSize(600, 600);
    glutInitWindowPosition(100, 100);
    glutCreateWindow("Bresenham Circle in All Quadrants with Axes");

    init();
    glutDisplayFunc(display);
    glutMainLoop();

    return 0;
}

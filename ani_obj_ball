#include <GL/glut.h>
#include <math.h>

float ballX = 0.0f;
float ballY = 0.0f;
float speedX = 0.01f;
float radius = 0.1f;

void drawCircle(float cx, float cy, float r) {
    glBegin(GL_TRIANGLE_FAN);
    glColor3f(1.0, 0.5, 0.0); // Orange color
    glVertex2f(cx, cy); // center
    for (int i = 0; i <= 100; i++) {
        float angle = 2 * 3.1416 * i / 100;
        glVertex2f(cx + cos(angle) * r, cy + sin(angle) * r);
    }
    glEnd();
}

void display() {
    glClear(GL_COLOR_BUFFER_BIT);
    drawCircle(ballX, ballY, radius);
    glFlush();
}

void update(int value) {
    ballX += speedX;

    // Bounce on edges
    if (ballX + radius > 1.0 || ballX - radius < -1.0) {
        speedX = -speedX; // reverse direction
    }

    glutPostRedisplay(); // Redraw
    glutTimerFunc(16, update, 0); // roughly 60 FPS
}

void init() {
    glClearColor(0.0, 0.0, 0.0, 1.0); // Black background
    glMatrixMode(GL_PROJECTION);
    gluOrtho2D(-1.0, 1.0, -1.0, 1.0); // 2D projection
}

int main(int argc, char** argv) {
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
    glutInitWindowSize(600, 600);
    glutInitWindowPosition(100, 100);
    glutCreateWindow("Ball Animation..");
    init();
    glutDisplayFunc(display);
    glutTimerFunc(0, update, 0); // Start timer
    glutMainLoop();
    return 0;
}

# Teapot
# 컴퓨터공학과 20210817 신현진

------------
//코드

    #include <GL/glut.h>
    
    float angleX = 0.0f; // x축 회전 각도
    float angleY = 0.0f; // y축 회전 각도
    
    void myDisplay() {
        glClearColor(1, 1, 1, 1); 
        glClear(GL_COLOR_BUFFER_BIT); 
    
        glLoadIdentity();
    
        glRotatef(angleX, 1.0f, 0.0f, 0.0f); // x축을 중심으로 회전
        glRotatef(angleY, 0.0f, 1.0f, 0.0f); // y축을 중심으로 회전
    
        glColor3f(0, 0, 0); 
        glutWireTeapot(0.5); 
    
        glFlush(); 
    }
    
    void update(int value) {
        angleX += 1.0f; 
        angleY += 2.0f; 
        if (angleX > 360) {
            angleX -= 360; 
        }
        if (angleY > 360) {
            angleY -= 360; 
        }
    
        glutPostRedisplay(); 
        glutTimerFunc(16, update, 0); 
    }
    
    int main(int ac, char** av) {
        glutInit(&ac, av); 
        glutInitDisplayMode(GLUT_RGB); 
        glutCreateWindow("draw"); 
        glutDisplayFunc(myDisplay); 
    
        glutTimerFunc(16, update, 0); 
    
        glutMainLoop(); 
    
        return 0;
    }

# Teapot
# 컴퓨터공학과 20210817 신현진

------------

https://github.com/Embarcadero/Dev-Cpp/assets/153504478/4d8da0df-315b-4b43-b5bc-144c326f078e

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

----------------

소감 : 

처음으로 Dev-C++을 사용하여 openGL로 그래픽스를 구현했는데 처음엔 p5.js랑 똑같을줄알았습니다. 하지만 모두 그래픽 처리와 관련된 라이브러리 또는 프레임워크이지만, 사용되는 언어와 API 등이 다르기 때문에 코드는 서로 다르다는것을 알게되었습니다. 실제로 코드를 보면서 p5.js 랑 많이 다른것을 느꼈고 실행도 하는것에 어려움을 많이 겪었습니다. 하지만 주전자를 만드는것은 p5.js로 만드는것은 어려운데 openGL에는 함수가 따로있어서 굉장히 편하다는것을 느꼈습니다. 그래서 어쩌면 openGL로 구현하는 것은 p5.js 보다 더욱 많은것을 구한할수있을거같다 라는 생각을 가졌습니다. 그래서 강의동안 openGL에대해 많이 배우고 실습하면서 더 다양한 디자인을 구현할수있도록 노력하겠습니다.


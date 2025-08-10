#include <iostream>
#include<windows.h>
#include<stdio.h>
#include<GL/glut.h>
#include<math.h>
#define pi 3.142857
#include<iostream>
using namespace std;

//boat
  float boatX=100;
  float boatY=150;
//boat 2
  float boat2X=1000;
  float boat2Y=10;
//boat 3
  float boat3X=500;
  float boat3Y=200;
//sun
  float circleX=900;
  float circleY=900;
  float circleZ=50;
//cloud 1
  float circle2X=40;
  float circle2Y=850;
  float circle2Z=50;
//cloud 2
  float circle3X=50;
  float circle3Y=860;
  float circle3Z=50;

  bool Direction=1;




//sun
void circle(float x1,float y1,float radius){
  float x=x1;
  float y=y1;


  //float radius=20;
  double pii=3.1416;
  glBegin(GL_TRIANGLE_FAN);
  glColor3ub(252, 143, 40);
  glVertex2f( x,y );
  for(int i=0;i<=360;i++){  ///i=0,1,2      360

    glColor3ub(252, 143, 40);

    float a=x+radius*cos(i*(pii/180));
    float b=y+radius*sin(i*(pii/180));
    glVertex2f( a,b);


  }
  glEnd();
}


//cloud 1
void circle2(float x1,float y1,float radius){
  float x=x1;
  float y=y1;


  //float radius=20;
  double pii=3.1416;
  glBegin(GL_TRIANGLE_FAN);
  glColor3ub(255, 255, 255);
  glVertex2f( x,y );
  for(int i=0;i<=360;i++){  ///i=0,1,2      360

    glColor3ub(255,255,255);

    float a=x+radius*cos(i*(pii/180));
    float b=y+radius*sin(i*(pii/180));
    glVertex2f( a,b);


  }
  glEnd();
}


//cloud 2
void circle3(float x1,float y1,float radius){
  float x=x1;
  float y=y1;


  //float radius=20;
  double pii=3.1416;
  glBegin(GL_TRIANGLE_FAN);
  glColor3ub(255, 255, 255);
  glVertex2f( x,y );
  for(int i=0;i<=360;i++){  ///i=0,1,2      360

    glColor3ub(255,255,255);

    float a=x+radius*cos(i*(pii/180));
    float b=y+radius*sin(i*(pii/180));
    glVertex2f( a,b);


  }
  glEnd();
}



void myInit ()
{

	//glClearColor(0.0, 1.0, 0.0, 0.0);
	//glClearColor(184.0f/255.0f, 213.0f/255.0f, 238.0f/255.0f, 1.0f);
	//glColor3f(0.0, 0.2, 0.0);
	glClearColor(128.0f/255.0f,0, 0, 1.0f);

	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();


	// setting window dimension in X- and Y- direction
	glOrtho(0, 1000, 0, 1000, -10.0, 10.0);


}

//sky
void sky(float x,float y){

glBegin(GL_QUADS);
glColor3ub(2,44,94);
glVertex2f( x,y );//pivot 0,600
glColor3ub(30,147,191);
glVertex2f( x+1000, y );
glColor3ub(30,147,191);
glVertex2f( x+1000, y+400);
glColor3ub(2,44,94);
glVertex2f( x, y+400);
glEnd();

}

//soil
void soil(float x,float y){

glBegin(GL_QUADS);
glColor3ub(225,116,59);
glVertex2f( x,y );//pivot 0,250
glColor3ub(225,116,59);
glVertex2f( x+1000, y+150 );
glColor3ub(225,116,59);
glVertex2f( x+1000, y+350);
glColor3ub(128, 65, 6);
glVertex2f( x, y+350);
glEnd();
}

//tree
void tree(float x,float y){

//uper
glBegin(GL_TRIANGLES);
glColor3ub(27, 199, 24);
glVertex2f( x,y );//795,500
glVertex2f( x+70, y );
glVertex2f( x+33, y+60);
glEnd();
//middle
glBegin(GL_TRIANGLES);
glColor3ub(24, 179, 21);
glVertex2f( x,y-20 );//795,500
glVertex2f( x+70, y-20 );
glVertex2f( x+33, y+40);
glEnd();
//down
glBegin(GL_TRIANGLES);
glColor3ub(20, 148, 18);
glVertex2f( x,y-40 );//795,500
glVertex2f( x+70, y-40 );
glVertex2f( x+33, y+20);
glEnd();
//tree main
glBegin(GL_QUADS);
glColor3ub(0,0,0);
glVertex2f( x+30,y-80 );
glVertex2f( x+40, y-80 );
glVertex2f( x+40, y-40);
glVertex2f( x+30, y-40);
glEnd();
}

//home 2
void home2(float x,float y){


//main
glBegin(GL_QUADS);
glColor3ub(128,0,0);
glVertex2f( x,y );//pivot 500,440
glVertex2f( x+150, y );
glVertex2f( x+150, y+100);
glVertex2f( x, y+100);
glEnd();

//roof
glBegin(GL_QUADS);
glColor3ub(0,0,0);
glVertex2f( x-20,y+100 );
glVertex2f( x+150, y+100 );
glVertex2f( x+190, y+170);
glVertex2f( x+20, y+170);
glEnd();

//right home face
glBegin(GL_POLYGON);
glColor3f(97, 10, 209);
glVertex2f( x+150,y );//500,440
glVertex2f( x+220, y );
glVertex2f( x+220,y+100);
glVertex2f( x+180,y+160);
glVertex2f( x+150, y+100 );
glEnd();


//right face roof

glBegin(GL_QUADS);
glColor3ub(0,0,0);
glVertex2f( x+220,y+100 );//500,440
glVertex2f( x+230, y+100 );
glVertex2f( x+190, y+170);
glVertex2f( x+180, y+160);
glEnd();
//gate
glBegin(GL_QUADS);
glColor3ub(0,0,0);
glVertex2f( x+170,y );
glVertex2f( x+200, y );
glVertex2f( x+200, y+75);
glVertex2f( x+170, y+75);
glEnd();

//window 1
glBegin(GL_QUADS);
glColor3ub(0,0,0);
glVertex2f( x+20,y+50 );//500,440
glVertex2f( x+70, y+50 );
glVertex2f( x+70, y+80);
glVertex2f( x+20, y+80);
glEnd();

//window 2
glBegin(GL_QUADS);
glColor3ub(0,0,0);
glVertex2f( x+80,y+50 );
glVertex2f( x+130, y+50 );
glVertex2f( x+130, y+80);
glVertex2f( x+80, y+80);
glEnd();
}

//house
void home(float x,float y){

//main
glBegin(GL_QUADS);
glColor3ub(97, 10, 209);
glVertex2f( x,y );//pivot 130,320
glVertex2f( x+170, y );
glVertex2f( x+170, y+100);
glVertex2f( x, y+100);
glEnd();
//roof
glBegin(GL_TRIANGLES);
glColor3f(0,0,0);
glVertex2f( x-5,y+100 );
glVertex2f( x+175, y+100 );
glVertex2f( x+85, y+160);
glEnd();
//gate
glBegin(GL_QUADS);
glColor3ub(227, 186, 36);
glVertex2f( x+20,y );//130,320
glVertex2f( x+60, y );
glVertex2f( x+60, y+60);
glVertex2f( x+20, y+60);
glEnd();

//window1
glBegin(GL_QUADS);
glColor3ub(227, 186, 36);
glVertex2f( x+90, y+40);//130,320
glVertex2f( x+150, y+40);
glVertex2f( x+150, y+70);
glVertex2f( x+90, y+70);
glEnd();

//main2

glBegin(GL_QUADS);
glColor3ub(100, 0, 250);
glVertex2f( x-60,y );//130,320
glVertex2f( x, y );
glVertex2f( x, y+60);
glVertex2f( x-60,y+60);
glEnd();
//main2 roof
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x-70,y+60 );//130,320
glVertex2f( x, y+60 );
glVertex2f( x, y+70);
glVertex2f( x-65, y+70);
glEnd();
//window2
glBegin(GL_QUADS);
glColor3ub(227, 186, 36);
glVertex2f( x-45,y+30 );//130,320
glVertex2f( x-15, y+30 );
glVertex2f( x-15, y+50);
glVertex2f( x-45, y+50);
glEnd();
}


//pani
void pani(float x,float y){

glBegin(GL_QUADS);
glColor3ub(19,89,104);
glVertex2f( x,y );//pivot 0,0
glColor3ub(19,89,104);
glVertex2f( x+1000, y );
glColor3ub(157,187,198);
glVertex2f( x+1000, y+400);
glColor3ub(157,187,198);
glVertex2f( x, y+250);
glEnd();
}


//ship
void boat(float x,float y){

//body
glBegin(GL_QUADS);
glColor3ub(7,21,30);
glVertex2f( x,y);//pivot 100,100
glVertex2f( x+100, y );
glVertex2f( x+130, y+30);
glVertex2f( x-30, y+30);
glEnd();
//Triangle
glBegin(GL_TRIANGLES);
glColor3ub(140, 45, 24);
glVertex2f( x-50,y+31);
glVertex2f( x+50, y+31 );
glVertex2f( x+50, y+80);
glEnd();

//pipe 1
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x+60,y+30 );
glVertex2f( x+70, y+30 );
glVertex2f( x+70, y+80);
glVertex2f( x+60, y+80);
glEnd();

//pipe 2
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x+80,y+30 );
glVertex2f( x+90, y+30 );
glVertex2f( x+90, y+80);
glVertex2f( x+80, y+80);
glEnd();

}


//ship2
void boat2(float x,float y){

//body
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x,y);//pivot 100,100
glVertex2f( x+50, y );
glVertex2f( x+80, y+20);
glVertex2f( x-30, y+20);
glEnd();


//Triangle
glBegin(GL_TRIANGLES);
glColor3ub(240, 91, 5);
glVertex2f( x+37,y+21);
glVertex2f( x+95, y+21 );
glVertex2f( x+37, y+57);
glEnd();


//pipe 1
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x+10,y+20 );
glVertex2f( x+20, y+20 );
glVertex2f( x+20, y+55);
glVertex2f( x+10, y+55);
glEnd();

//pipe 2
glBegin(GL_QUADS);
glColor3ub(0, 0,0);
glVertex2f( x+25,y+20 );
glVertex2f( x+35, y+20 );
glVertex2f( x+35, y+55);
glVertex2f( x+25, y+55);
glEnd();

}
//boat 3
void boat3(float x,float y){

//body
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x,y);//pivot 100,100
glVertex2f( x+50, y );
glVertex2f( x+80, y+20);
glVertex2f( x-30, y+20);
glEnd();


//Triangle
glBegin(GL_TRIANGLES);
glColor3ub(29, 15, 219);
glVertex2f( x+37,y+21);
glVertex2f( x+95, y+21 );
glVertex2f( x+37, y+57);
glEnd();


//pipe 1
glBegin(GL_QUADS);
glColor3ub(0, 0, 0);
glVertex2f( x+10,y+20 );
glVertex2f( x+20, y+20 );
glVertex2f( x+20, y+55);
glVertex2f( x+10, y+55);
glEnd();

//pipe 2
glBegin(GL_QUADS);
glColor3ub(0, 0,0);
glVertex2f( x+25,y+20 );
glVertex2f( x+35, y+20 );
glVertex2f( x+35, y+55);
glVertex2f( x+25, y+55);
glEnd();

}



//pahar
void pahar(float x,float y){
    glBegin(GL_TRIANGLES);
glColor3ub(23, 66, 16);
glVertex2f( x,y );//pivot 0,600
glVertex2f( x+100, y );
glVertex2f( x+50, y+90);
glEnd();
}

//pahar 1
void pahar1(float x,float y){
    glBegin(GL_TRIANGLES);
glColor3ub(32, 97, 21);
glVertex2f( x,y );//pivot 0,600
glVertex2f( x+160, y );
glVertex2f( x+80, y+130);
glEnd();
}



void display ()
{



glClear(GL_COLOR_BUFFER_BIT);




//sky
sky(0,600);


//Sun
circle(circleX,circleY,circleZ);


//cloud1
circle2(circle2X,circle2Y,circle2Z);
circle2(circle2X+50,circle2Y,circle2Z);
circle2(circle2X+100,circle2Y,circle2Z);
circle2(circle2X+25,circle2Y+50,circle2Z);
circle2(circle2X+75,circle2Y+50,circle2Z);


//cloud2
circle3(circle3X+400,circle3Y-80,circle3Z);
circle3(circle3X+450,circle3Y-80,circle3Z);
circle3(circle3X+500,circle3Y-80,circle3Z);
circle3(circle3X+425,circle3Y-130,circle3Z);
circle3(circle3X+475,circle3Y-130,circle3Z);


//soil
soil(0,250);


tree(290,420);
//house
home(130,320);


//pahar
pahar(0,600);
pahar(80,600);
pahar(170,600);
pahar(370,600);
pahar1(240,600);
pahar(450,600);
pahar(620,600);
pahar1(510,600);
pahar(700,600);
pahar(770,600);
pahar(840,600);
pahar(910,600);


//pani
pani(0,0);


//boat
boat(boatX,boatY);

//boat 2
boat2(boat2X,boat2Y);

//boat 3
boat3(boat3X,boat3Y);



//tree
tree(500,650);
tree(400,550);

//home 2
home2(550,470);
home2(450,420);

//tree
tree(795,500);
tree(50,580);
tree(150,580);
tree(250,580);
tree(850,580);




/*

//Quads
glBegin(GL_QUADS);
glColor3ub(128,0,0);
glVertex2f( 0,0 );
glVertex2f( 200, 0 );
glVertex2f( 200, 200);
glVertex2f( 0, 200);
glEnd();

//Triangle
glBegin(GL_TRIANGLES);
glColor3f(0,0,0);
glVertex2f( 250,250 );
glVertex2f( 300, 200 );
glVertex2f( 200, 200);
glEnd();

//circle(100,100,20);

//lines
glBegin(GL_LINES);
glColor3f(0,1,0);
glVertex2f( 250,500 );
glVertex2f( 250, 0 );
glEnd();

//point

glPointSize(100);
glBegin(GL_POINTS);
glColor3f(0,1,0);
glVertex2f( 100,100 );
glEnd();

//Quads
glBegin(GL_QUADS);
glColor3ub(128,0,0);
glVertex2f( 0,0 );
glVertex2f( 200, 0 );
glVertex2f( 200, 200);
glVertex2f( 0, 200);
glEnd();

//polygon
glBegin(GL_POLYGON);
glColor3f(0,1,0);
glVertex2f( 100,100 );
glVertex2f( 100, 0 );
glVertex2f( 50, 0 );
glVertex2f( 10, 50 );
glVertex2f( 50, 200 );

glEnd();

*/




glFlush();
}
void my_keyboard(unsigned char key, int x, int y)
{
    cout<<key<<endl;
    if(key=='w'){
        boatY+=10;
        if(boatY>200){
            boatY=200;
        }
    }
    if(key=='z'){
        boatY-=10;
        if(boatY<0){
            boatY=0;
        }

    }
    if(key=='a'){
        boatX-=10;
        if(boatX<0){
            boatX=0;
        }
    }
    if(key=='d'){
        boatX+=10;
        if(boatX>1000){
            boatX=1000;
        }
    }

}


void update(int value) {

    //moonY=moonY+0.9;

	//cout<<moonY<<endl;


	//boat
    boatX+=0.5;
    if(boatX>1200){
        boatX=-120;
        boatY=120;
    }

     //boat 2 with random
     boat2X-=1.3;
     if(boat2X < -50){
         boat2X=1200;
         boat2Y=10+rand()%150;
     }
     //boat 3 with random
     boat3X-=2;
     if(boat3X < -50){
         boat3X=1200;
         boat3Y=50+rand()%200;
     }



     //collision from gpt


       if (fabs(boatX - boat2X) < 120 && fabs(boatY - boat2Y) <30) {
        // Collision detected
        //boatX = -120;  // Reset boat position
        boat2X = 1200; // Reset boat 2 position
        //boatY = 120;
        //boat2Y = 10 + rand() % 150;
    }

    // Check collision between boat and boat 3

    if (fabs(boatX - boat3X) < 120 && fabs(boatY - boat3Y) < 30) {
        // Collision detected
       // boatX = -120;  // Reset boat position
        boat3X = 1200; // Reset boat 3 position
       // boatY = 120;
       // boat3Y = 50 + rand() % 200;
    }
    /*

    // Check collision between boat2 and boat3
    if (fabs(boat2X - boat3X) < 50 && fabs(boat2Y - boat3Y) < 30) {
        // Collision detected
        boat2X = 1200; // Reset boat2 position
        boat3X = 1200; // Reset boat3 position
        boat2Y = 10 + rand() % 150;
        boat3Y = 50 + rand() % 200;
    }
    */




    //sun
    circleX-=0.20;
    circleY-=0.1;
    if(circleY<500){
        circleX=900;
        circleY=1000;
    }



    //cloud 1
    circle2X+=0.3;
    if(circle2X>1000){
        circle2X=-300;
    }

    //cloud 2
    circle3X+=0.5;
    if(circle3X>1000){
        circle3X=-600;
    }



	glutPostRedisplay();
	glutTimerFunc(25, update, 0);
}

int main (int argc, char** argv)
{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);

	// giving window size in X- and Y- direction
	glutInitWindowSize(500, 500);
	glutInitWindowPosition(100, 0);

	// Giving name to window
	glutCreateWindow("bahubali 3");
	myInit();

    glutDisplayFunc(display);
    glutKeyboardFunc(my_keyboard);
	glutTimerFunc(25, update, 0);

	//glutTimerFunc(25, update, 0);

	glutMainLoop();
}



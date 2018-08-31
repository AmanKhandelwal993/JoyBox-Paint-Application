#include<graphics.h>
#include<conio.h>
#include<stdio.h>
#include<dos.h>

union REGS i, o;

void line();
void rectangle();
void circle();
void brush();
void ellipse();
void eraser();
void pencil();
void tools();
void start();
void linetheme();
int linewidth();
int linestyle();

// configuring mouse cursor in the window --------------
int initmouse()
{
   i.x.ax = 0;
   int86(0X33,&i,&o);
   return ( o.x.ax );
}
void showmouseptr()
{
   i.x.ax = 1;
   int86(0X33,&i,&o);
}
void hidemouseptr()
{
   i.x.ax = 2;
   int86(0X33,&i,&o);
}
void getmousepos(int *button, int *x, int *y)
{
   i.x.ax = 3;
   int86(0X33,&i,&o);

   *button = o.x.bx;
   *x = o.x.cx;
   *y = o.x.dx;
}
//----------------------------------------------

// Creating Theme Of the Application ( making G.U.I.)------------
void theme()
{
	// clear box of tool heading
	setcolor(BLACK);
	setfillstyle(SOLID_FILL,BLACK);
	bar(5,30,65,435);
	 //  delay(1000);
	showmouseptr();
	setcolor(BLACK);
	setfillstyle(SOLID_FILL,BLACK);
	bar(8,55,62,435);
	setcolor(WHITE);
	setfillstyle(SOLID_FILL,WHITE);
	//SETTING  DEFAULT   line
	setlinestyle(SOLID_LINE,0x3333,1);
	int a,b;
	a=getmaxx();
	b=getmaxy();
	rectangle(0,0,a,b); //boundary of the page
	line(70,0,70,b);    // line seperating paint screen and tool bar
	// paint tile box
	rectangle(5,5,65,25);
	settextstyle(SMALL_FONT, HORIZ_DIR, 7);
	outtextxy(8,4,"PAINT");
	// box for tool heading
	rectangle(5,30,65,50);
	rectangle(5,30,65,255);
	settextstyle(SMALL_FONT, HORIZ_DIR, 5);
	outtextxy(15,32,"TOOLS");
	// box for line tool
	rectangle(8,55,62,75);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,60,"LINE");
	// box for circle tool
	rectangle(8,80,62,100);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,85,"CIRCLE");
	// box for rectangle tool
	rectangle(8,105,62,125);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,110,"RECTANGL");
	// box for ellipse tool
	rectangle(8,130,62,150);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,135,"ELLIPSE");
	// box for eraser tool
	rectangle(8,155,62,175);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,160,"ERASER");
	// box for brush tool
	rectangle(8,180,62,200);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,185,"BRUSH");
	// box for text writing tool
	rectangle(8,205,62,225);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,210,"TEXT");
	//box for pencil tool
	rectangle(8,230,62,250);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,235,"PENCIL");


       //	circle(15,250,10);
       //	circle(40,250,10);
}
void linetheme()
{
       // clear box of tool heading
	setcolor(BLACK);
	setfillstyle(SOLID_FILL,BLACK);
	bar(5,30,65,255);
     //  delay(1000);
     // clear something but in mystery but no use till now
	showmouseptr();
	setcolor(BLACK);
	setfillstyle(SOLID_FILL,BLACK);
	bar(8,55,62,75);
	setcolor(WHITE);
	setfillstyle(SOLID_FILL,WHITE);

	// box for tool heading
	rectangle(5,30,65,50);
	settextstyle(SMALL_FONT, HORIZ_DIR, 5);
	outtextxy(15,32,"TOOLS");

	// box for line tool
	rectangle(8,55,62,75);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,60,"LINE");

	//choose width of line
	rectangle(5,80,65,140);
	rectangle(8,85,62,105);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,90,"WIDTH");

	//box for width set
	//normal line
	rectangle(8,110,62,120);
	setlinestyle(SOLID_LINE,0x3333,1);
	line(10,115,60,115);

	//thick line
	rectangle(8,125,62,135);
	setlinestyle(SOLID_LINE,0x3333,3);
	line(10,130,60,130);
	setlinestyle(SOLID_LINE,0x3333,1);

	//choose style of line
	rectangle(5,145,65,215);
	rectangle(8,150,62,170);
	settextstyle(SMALL_FONT, HORIZ_DIR, 4);
	outtextxy(11,155,"STYLE");

	//box for style set
	//solid line
	rectangle(8,175,62,185);
	setlinestyle(SOLID_LINE,0x3333,1);
	line(10,180,60,180);
	setlinestyle(SOLID_LINE,0x3333,1);

	//dotted line
	rectangle(8,190,62,200);
	setlinestyle(DOTTED_LINE,0x3333,1);
	line(10,195,60,195);
	setlinestyle(SOLID_LINE,0x3333,1);

	//dashed line
	rectangle(8,205,62,215);
	setlinestyle(DASHED_LINE,0x3333,1);
	line(10,210,60,210);
	setlinestyle(SOLID_LINE,0x3333,1);
}

// function that set the width of the line when called -------------------
int linewidth(int x, int y)
{
	int linew;
	showmouseptr();
	if(x>8&&y>110&&x<62&&y<120)
	{
	      setlinestyle(SOLID_LINE,0x3333,3);
	      line(10,130,60,130);
	      setlinestyle(SOLID_LINE,0x3333,1);
	      setcolor(5);
	      line(10,115,60,115);
	      setcolor(15);
	      linew=1;
	}
	else if(x>8&&y>125&&x<62&&y<135)
	{
	      setlinestyle(SOLID_LINE,0x3333,1);
	      line(10,115,60,115);
	      setlinestyle(SOLID_LINE,0x3333,3);
	     // showmouseptr();
	      setcolor(5);
	      //showmouseptr();
	      line(10,130,60,130);
	      setcolor(15);
	      linew=3;
	}
	return(linew);
}
//-------------------------------------------------------

//function that set the style of the line when called --------------------
int linestyle(int x, int y)
{
	int line_sty;
	showmouseptr();
	//solid line button working
	if(x>8&&y>175&&x<62&&y<185)
	{
		// dotted line switch off
	      setlinestyle(DOTTED_LINE,0x3333,1);
	      line(10,195,60,195);
	       //  dashed line switch off
	       setlinestyle(DOTTED_LINE,0x3333,1);
	      line(10,210,60,210);
	      // solid line switch on
	      setlinestyle(SOLID_LINE,0x3333,1);
	      setcolor(5);
	      line(10,180,60,180);
	      setcolor(15);
	      line_sty=0;
	}
	//dotted line button working
	else if(x>8&&y>190&&x<62&&y<200)
	{
		// solid line switch off
	      setlinestyle(SOLID_LINE,0x3333,1);
	      line(10,180,60,180);
	       //  dashed line switch off
	       setlinestyle(DOTTED_LINE,0x3333,1);
	      line(10,210,60,210);
	      // solid line switch on
	      setlinestyle(DOTTED_LINE,0x3333,1);
	      setcolor(5);
	      line(10,195,60,195);
	      setcolor(15);
	      line_sty=1;
	}
	//dashed line button working
	else if(x>8&&y>205&&x<62&&y<215)
	{
		// dotted line switch off
	      setlinestyle(DOTTED_LINE,0x3333,1);
	      line(10,195,60,195);
	       //  solid line switch off
	       setlinestyle(DOTTED_LINE,0x3333,1);
	      line(10,180,60,180);
	      // dashed line switch on
	      setlinestyle(SOLID_LINE,0x3333,1);
	      setcolor(5);
	      line(10,210,60,210);
	      setcolor(15);
	      line_sty=3;
	}
	return(line_sty);
}
//-------------------------------------------------------------------

//This
void tools()
{
   int status, button, x, y,a,b;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		//line call
		if( button == 1 &&x>8&&y>55&&x<62&&y<75)
		{
			button = -1;
			linetheme();
			line();
		}
		//circle call
		else if( button == 1 &&x>8&&y>80&&x<62&&y<100)
		{
			button = -1;
		       //	circle();
		}
		//rectangle call
		else if( button == 1 &&x>8&&y>105&&x<62&&y<125)
		{
			button = -1;
		      //	rectangle();
		}
		//ellipse call
		else if( button == 1 &&x>8&&y>130&&x<62&&y<150)

		{
			button = -1;
		       //	ellipse();
		}
		//eraser  call
		else if( button == 1 &&x>8&&y>155&&x<62&&y<175)
		{
			button = -1;
			 eraser();
		}
		//brush  call
		else if( button == 1 &&x>8&&y>180&&x<62&&y<200)
		{
			button = -1;
			brush();
		}
		//pencil call
		else if( button == 1 &&x>8&&y>230&&x<62&&y<250)
		{
			button = -1;
			pencil();
		}

	     /*	else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		} */
      }
}
}

void brush()
{
   int status, button, x, y,a,b;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();

   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if( button == 1 && x>70)
		{
			button = -1;
			setcolor(15);
			setfillstyle(SOLID_FILL,WHITE);
			hidemouseptr();
		       bar(x,y,x+5,y+5);
		       showmouseptr();
		}
	   /*	else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}        */
		else if( button==1 && x>0 && x<70 && y>0 && y<439)
		{
			tools();
		}
      }
}
}
/*
void rectangle()
{
   int status, button, x, y,a,b;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if( button == 1 && x>70)
		{
			button = -1;
			 bar(x,y,x+10,y+10);
		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		else
		{
			tools();
		}
      }
}
}    */
// coding for the pencil tool done perfectly
void pencil()
{
   int status, button, x, y,a,b,initx,inity,endx,endy,cl=0,cl1=0,cl2=1,linew;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if(button!=1 && cl1>0)
		{
			initx=0;
			inity=0;
			endx=0;
			endy=0;
			cl1=0; // tell that the continuation of pressing mouse button to draw a line is stop
			cl2=1; //flag telling whether the line button has stop by user
		}
	       else if( button == 1 && x>70)
		{
			button = -1;
			if( cl2==1)
			{
				initx=x;
				inity=y;
				endx=x;
				endy=y;
				cl2=0;// it tells that one time we hane given value of initial and end point same as x & y
			}
			if(cl2==0)
			{
			if( cl==0)
			{

				initx=x;
				inity=y;
			       cl=1;  // falg tells switching b/w initial point and end point
			}
			else if(cl==1)
			{
				endx=x;
				endy=y;
				cl=0;
			}
			}
		       //	cl++;
		       cl1++;
		       hidemouseptr();
			line(initx,inity,endx,endy);
			showmouseptr();
		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		//for going to tools bar
		else if( button==1 && x>0 && x<70 && y>0 && y<439)
		{
			tools();
		}
		//for going to width
		else if( button==1 && x>0 && x<70 && y>0 && y<439)
		{
			linew=linewidth(x,y);

		}

      }
}
}
void line()
{
	delay(1000);
   int status, button, x, y,a,b,initx,inity,endx,endy,cl=0,cl1=0,cl2=1,w1=0,linew=1,line_sty=0
   ;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
     // setcolor(BLACK);
     // setfillstyle(SOLID_FILL,BLACK);
     // bar(8,55,62,75);
     // theme();
      while(!kbhit())
      {
		if(w1=1);
		delay(500);
	       //	delay(3);
		getmousepos(&button,&x,&y);
		if(button!=1)
		goto le;

	      /*if(cl==2)
		{
			line(initx,inity,endx,endy);
			initx=0;
			inity=0;
			endx=0;
			endy=0;
			cl=0;
			w1=0;
		    //	delay(5);
		} */
	       /*	if(button!=1 && cl1>1)
		{
			initx=0;
			inity=0;
			endx=0;
			endy=0;
			cl1=0; // tell that the continuation of pressing mouse button to draw a line is stop
			cl2=1; //flag telling whether the line button has stop by user
			w1=0;
		}   */
	       if( button == 1 && x>70)
		{
			button = -1;
			if( cl2==1)
			{
				initx=x;
				inity=y;
				endx=x;
				endy=y;
				cl2=0;// it tells that one time we hane given value of initial and end point same as x & y
			}
			if(cl2==0)
			{
			if( cl==0)
			{

				initx=x;
				inity=y;
			      // cl=1;  // falg tells switching b/w initial point and end point
				setlinestyle(SOLID_LINE,0x3333,1);
				circle(15,250,10);
				setlinestyle(line_sty,0x3333,linew);
			}
			else if(cl==1)
			{
				endx=x;
				endy=y;
			      //	cl=0;
				circle(40,250,10);
			}
			}
		       cl++;
		       cl1++;
		       w1++;
		       //	line(initx,inity,endx,endy);
		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		else if( button==1 && x>5 && y>30 && x<65 && y<50)
		{
			button=-1;
			tools();
		}
		//for going to width
		else if( button==1 && x>5 && x<80 && y>65 && y<140 )
		{
			button=-1;
			showmouseptr();
			linew=linewidth(x,y);

		}
		else if( button==1 && x>5 && x<145 && y>65 && y<215 )
		{
			button=-1;
			line_sty=linestyle(x,y);

		}
		if(cl==2)
		{
			hidemouseptr();
			line(initx,inity,endx,endy);
			showmouseptr();
			initx=0;
			inity=0;
			endx=0;
			endy=0;
			cl=0;
			w1=0;
			setcolor(BLACK);

			circle(15,250,10);
			circle(40,250,10);
			setcolor(WHITE);
		    //	delay(5);
		}
	      // w1++;
	      le:
      }
}
}
/*
void circle()
{
   int status, button, x, y,a,b;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if( button == 1 && x>70)
		{
			button = -1;
		       bar(x,y,x+10,y+10);
		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		else
		{
			tools();
		}
      }
}
}
void ellipse()
{
   int status, button, x, y,a,b;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if( button == 1 && x>70)
		{
			button = -1;
		       bar(x,y,x+10,y+10);
		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		else
		{
			tools();
		}
      }
}
} */
void eraser()
{
   int status, button, x, y,a,b;
   char array[50];
   status = initmouse();
   a=getmaxx();
   b=getmaxy();
   if ( status == 0 )
   printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if( button == 1 && x>70)
		{
			button = -1;
			setcolor(BLACK);
			setfillstyle(SOLID_FILL,BLACK);
			hidemouseptr();
			bar(x,y,x+20,y+20);
			showmouseptr();
			setcolor(WHITE);
			setfillstyle(SOLID_FILL,WHITE);

		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		else if( button==1 && x>0 && x<70 && y>0 && y<439)
		{
			tools();
		}
      }
}
}
void start()
{
	int i;
	for(i=1;i<15;i++)
	{
	settextstyle(BOLD_FONT, HORIZ_DIR, 6);
	settextstyle(4, HORIZ_DIR, 6);
	setcolor(i);
	outtextxy(200,30,"JOY BOX");
	outtextxy(150,100,"THE PAINT APP");

	settextstyle(0, HORIZ_DIR, 1);
	delay(500);
	}
	settextstyle(BOLD_FONT, HORIZ_DIR, 6);
	settextstyle(SCRIPT_FONT, HORIZ_DIR, 6);
	setcolor(5);
	outtextxy(180,137,"PAINT");
	settextstyle(0, HORIZ_DIR, 1);

}

int main()
{
   int gd = DETECT, gm, status, button=-1, x, y,a,b;
   char array[50];

   initgraph(&gd,&gm,"C:\\TC\\BGI");
   settextstyle(DEFAULT_FONT,0,2);

   status = initmouse();

   a=getmaxx();
   b=getmaxy();
   start();
   cleardevice();
   if ( status == 0 )
      printf("Mouse support not available.\n");
   else
   {
      showmouseptr();
      getmousepos(&button,&x,&y);
      theme();
      while(!kbhit())
      {
		getmousepos(&button,&x,&y);
		delay(5);
		if( button == 1 && x>70)
		{
			button = -1;
			hidemouseptr();
			bar(x,y,x+10,y+10);
			showmouseptr();
			//brush();
		}
		else if( button == 2 )
		{
			button = -1;
			cleardevice();
			sprintf(array,"Right Button clicked x = %d y = %d",x,y);
			outtext(array);
		}
		else if( button==1 && x>0 && x<70 && y>0 && y<439)
		{
		   tools();
		}
      }
}
getch();
closegraph();
return 0;
}

/*main()
{
   int gd = DETECT, gm, status, button, x, y,a,b;
   char array[50];

   initgraph(&gd,&gm,"C:\\TC\\BGI");
   settextstyle(DEFAULT_FONT,0,2);

   status = initmouse();

   a=getmaxx();
   b=getmaxy();
   rectangle(0,0,a,b);
   if ( status == 0 )
      printf("Mouse support not available.\n");
   else
   {
      showmouseptr();

      getmousepos(&button,&x,&y);
      rectangle(0,0,a,b);
      line(70,0,70,b);
      theme();
      while(!kbhit())
    // while(1)
      {
	 getmousepos(&button,&x,&y);
       //	  bar(x,y,x+10,y+10);
       //	   circle(x,y,20);

       //circle(x,y,50);
	delay(5);
	if( button == 1 && x>70)
	{
	   // button = -1;
	   // cleardevice();
	   // sprintf(array,"Left Button clicked x = %d y = %d",x,y);
	   // outtext(array);
		bar(x,y,x+10,y+10);
	 // circle(x,y,10);
	// delay(5);
	 }



	/* else if( button == 2 )
	 {
	    button = -1;
	    cleardevice();
	    sprintf(array,"Right Button clicked x = %d y = %d",x,y);
	    outtext(array);
	 } */
	// delay(5);
	// }

  /*    }
}


   getch();
   closegraph();
   return 0;
} */
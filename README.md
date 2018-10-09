
#include <iostream>
#include <fstream>

using namespace std;
// function to draw rectangle take parameters ( x : X axes dimension  , y : Y axes dimension , h : height , and the color of the bar )
void drawBar ( int x , int y ,int w , int h , string color = "blue" );
// functions to draw x , y axes
void drawXaxes ( int x1 , int y1 ,int x2 , int y2 , string color = "black" );
void drawYaxes ( int x1 , int y1 ,int x2 , int y2 , string color = "black" );

ofstream file ;

int main()
{

    file.open( "barchart.svg" , ios :: out );
    file << "<svg width = \"" << 400 << "\"" << " height = \"" << 400 << "\"" << endl;
    file << "xmlns=\"http://www.w3.org/2000/svg\">" << endl;

    /*  |(0,0)--------------------------------- (400,0)
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |(0,400)------------------------------- (400,400)*/

    drawXaxes ( 30 , 400 , 400 , 400 );
    drawYaxes( 30 , 0 , 30 , 400);


    /*  |(30,0)
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |
        |(30,400)------------------------------- (400,400)*/


    int x = 60 , w = 50 , h ,i = 1 ;
    while ( i <= 4 ){
    cout << " enter value" << i << " : " ;
    cin >> h ;
    if ( h > 0 ){ int y = 400-h ; drawBar(x , y , w , h) ; x += 80; }
    else{ cout << "Enter positive dimensions" << endl ; break;}
    i++; }

    file << "</svg>" << endl ;
    file.close();

    return 0;
}

void drawBar(int x , int y ,int w , int h , string color )
{
    file << "<rect x = \"" << x << "\"" << " y = \"" << y << "\"" << " width = \""
        << w << "\"" <<  " height = \"" << h << "\"" << endl;
    file << "style = \"fill:" << color << ";\"/>" << endl ;
}

void drawXaxes ( int x1 , int y1 ,int x2 , int y2 , string color ){
    file << "<line x1 = \""<< x1 << "\" y1= \"" << y1 << "\" x2= \"" << x2 << "\" y2= \"" << y2 << "\"" << endl;
    file << "style= \"" << "stroke:"<< color << ";" << "stroke-width:" << 2 << "\"/>" << endl;

}

void drawYaxes ( int x1 , int y1 ,int x2 , int y2 , string color ){
    file << "<line x1 = \""<< x1 << "\" y1= \"" << y1 << "\" x2= \"" << x2 << "\" y2= \"" << y2 << "\"" << endl;
    file << "style= \"" << "stroke:"<< color << ";" << "stroke-width:" << 2 << "\"/>" << endl;

}

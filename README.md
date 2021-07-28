# 8-channel-quiz-buzzer

8 Channel Quiz buzzer Circuit


Code:
#include <reg51.h> 

sbit rst = P3^3;
sbit buzzer= P3^0;
void delay(unsigned int rtime);
int poll(void);

int poll()
{
    char inp;
    P1 = 0xff;     //set p1 as input
    while(P1 == 0xff);
    inp = P1;
    P2 = 0xf0;

        if (inp==0xfe) // Button 1 is pressed.
        {
            P2=0xf9;
            buzzer=1;
            delay(500); // Activate buzzer for 1 second.
            buzzer=0;
        }
        
        else if (inp==0xfd) // Button 2 is pressed.
        {
            P2=0xa4;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
        else if (inp==0xfb) // Button 3 is pressed.
        {
            P2=0xb0;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
        else if (inp==0xf7) // Button 4 is pressed.
        {
            P2=0x99;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
        else if (inp==0xef) // Button 5 is pressed.
        {
            P2=0x92;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
        else if (inp==0xdf) // Button 6 is pressed.
        {
            P2=0x82;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
        else if (inp==0xbf) // Button 7 is pressed.
        {
            P2=0xf8;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
        else if (inp==0x7f) // Button 8 is pressed.
        {
            P2=0x80;
            buzzer=1;
            delay(500);
            buzzer=0;
            
        }
        
}



void delay(unsigned int rtime)
{
    unsigned int r, s;
    for (r = 0; r < rtime; r++)
        for (s = 0; s < 1275; s++);
}

void main(void)
{

    int n;
    P2 = 0xff;
    rst = 1;
    buzzer = 0;
    n = poll();
    delay(500);
    while(rst != 0);
    P2 = 0x00;
    delay(500);
    
}

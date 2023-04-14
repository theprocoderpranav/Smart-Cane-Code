# You_Cane_Do_It
This is the code to make a blind cane that can detect obstacles in front of it in less than 3 steps. 
I have used the MIT app inventor to display the messages on the mobile phone using bluetooth

Make sure to get these materials:
HC-05 Bluetooth Module
Ardiuno Uno r3
Mini Breadboard
Jumper Cables(Male to Male and Female to Male)
Button
MIT app inventor
http://ai2.appinventor.mit.edu/#6193708922699776



Now, lets get on to the code

MAKE SURE TO UPLOAD THIS ONLY IN ARDUINO!!!

#include <SoftwareSerial.h> 
SoftwareSerial bluetooth (5,6);
void setup ()
{
  Serial.begin(9600);
  bluetooth.begin(9600);
  pinMode(9, OUTPUT);
  pinMode(10,INPUT);
  pinMode(11, INPUT_PULLUP);
 
  
}
int attempt = 1;
void loop  ()
{
  
  digitalWrite(9,HIGH);
  delayMicroseconds(10);
  digitalWrite(9,LOW);
  long int duration = pulseIn(10, HIGH);

  long int distance = (0.033 * duration / 2);

  Serial.println(distance);

  int button = digitalRead(11);
  
 if (distance <= 91.44)
 {
   bluetooth.println("obstacle");
 } 
 else if(button == LOW)
 {
  bluetooth.println("emergency");
 }

  delay(2000);
}

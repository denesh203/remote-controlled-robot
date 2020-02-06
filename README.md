# remote-controlled-robot
#include <SoftwareSerial.h>
SoftwareSerial myserial(10,11);
int lm1=6;
int lm2=7;
int rm1=8;
int rm2=9;
void setup()
{
pinMode(lm1,OUTPUT);
pinMode(lm2,OUTPUT);
pinMode(rm1,OUTPUT);
pinMode (rm2,OUTPUT);
Serial.begin(9600);
myserial.begin(9600);
myserial.println("connect A B C or any other");
}
void loop()
{
if (myserial.available())
{
      int val=myserial.read();
      Serial.println(val);

if(val=='A')
 {
      digitalWrite(lm1,HIGH);
      digitalWrite(lm2,LOW);
      digitalWrite(rm1,HIGH);
      digitalWrite(rm2,LOW);
      Serial.println("\n Moving Forward");
 }
 else if(val=='B')
 {
      digitalWrite(lm1,LOW);
      digitalWrite(lm2,HIGH);
      digitalWrite(rm1,LOW);
      digitalWrite(rm2,HIGH);
      Serial.println("\n moving backward");
 }
 else if(val=='C')
 {
      digitalWrite(lm1,HIGH);
      digitalWrite(lm2,LOW);
      digitalWrite(rm1,LOW);
      digitalWrite(rm2,HIGH);
      Serial.println("\n moving left");
 }
 else if(val=='D')
 {
    digitalWrite(lm1,LOW);
    digitalWrite(lm2,HIGH);
    digitalWrite(rm1,HIGH);
    digitalWrite(rm2,LOW);
    Serial.println("\n now moving right");
 }
 else
{
  digitalWrite(lm1,LOW);
  digitalWrite(lm2,LOW);
  digitalWrite(rm1,LOW);
  digitalWrite(rm2,LOW);
  Serial.println(" \n now stop");
}
}
}

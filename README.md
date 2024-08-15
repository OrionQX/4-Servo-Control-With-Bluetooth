
#include <Servo.h> 
Servo myservo1, myservo2, myservo3, myservo4;

byte serialA;

void setup()
{
myservo1.attach(2);
myservo1.write(0);
myservo2.attach(3);
myservo2.write(0);
myservo3.attach(4);
myservo3.write(0);
myservo4.attach(5);
myservo4.write(0);

  Serial.begin(9600);
}

void loop()
{
  if (Serial.available() > 2) {serialA = Serial.read();Serial.println(serialA);}
  {
    unsigned int servopos = Serial.read();
    unsigned int servopos1 = Serial.read();
    unsigned int realservo = (servopos1 *256) + servopos; 
    Serial.println(realservo); 
    
    if (realservo >= 1000 && realservo <1180){
    int servo1 = realservo;
    servo1 = map(servo1, 1000,1180,0,180);
    myservo1.write(servo1);
    Serial.println("servo 1 ON");
    delay(10);

    }
    
    if (realservo >=2000 && realservo <2180){
      int servo2 = realservo;
      servo2 = map(servo2,2000,2180,0,180);
      myservo2.write(servo2);
      Serial.println("servo 2 On");
      delay(10);
      
    }
    
    if (realservo >=3000 && realservo < 3180){
      int servo3 = realservo;
      servo3 = map(servo3, 3000, 3180,0,180);
      myservo3.write(servo3);
      Serial.println("servo 3 On");
      delay(10);
    }
    if (realservo >=4000 && realservo < 4180){
      int servo4 = realservo;
      servo4 = map(servo4, 4000, 4180,0,180);
      myservo4.write(servo4);
      Serial.println("servo 4 On");
      delay(10);
    }
    

 
  }


}

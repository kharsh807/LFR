# LFR
LFR-Line Following Robot



![image](https://github.com/kharsh807/LFR/assets/121211344/1ce53c92-b77c-404d-9e36-03e0aceec33c)
## How to Build

1. **Assemble the Chassis**: Mount the motors and wheels onto the chassis.
2. **Install the Sensors**: Attach the IR sensors to the front of the robot, facing downward.
3. **Wiring**: Connect the motors to the motor driver and the IR sensors to the Arduino.
4. **Programming**: Upload the line-following code to the Arduino.
5. **Testing**: Place the robot on a track and test its ability to follow the line.


## Code
/*Run this code in arduino ide*/



void setup() {
  // put your setup code here, to run once:
//  Motor driver
pinMode(10,OUTPUT); //left motor
pinMode(11,OUTPUT); //left motor
pinMode(12,OUTPUT); //right motor
pinMode(13,OUTPUT); //right motor
pinMode(8,OUTPUT); //enable1
pinMode(9,OUTPUT); //enable2
pinMode(2,OUTPUT);
digitalWrite(2,HIGH);
digitalWrite(8,HIGH);
digitalWrite(9,HIGH);
//left sensor
pinMode(3,OUTPUT);
pinMode(4,OUTPUT);
pinMode(5,INPUT);
//mid sensor
pinMode(6,INPUT);
//right sensor
pinMode(7,INPUT);

digitalWrite(4,LOW);
digitalWrite(3,HIGH);



Serial.begin(9600);
}
 void forward()
{
  digitalWrite(10,HIGH);
  digitalWrite(11,LOW);
  digitalWrite(12,HIGH);
  digitalWrite(13,LOW);
  }
  

void left()
{
  digitalWrite(10,LOW);
  digitalWrite(11,LOW);
  digitalWrite(12,HIGH);
  digitalWrite(13,LOW);
  }
  void right()
{
  digitalWrite(10,HIGH);
  digitalWrite(11,LOW);
  digitalWrite(12,LOW);
  digitalWrite(13,LOW);
  }

   void steepleft()
{
  digitalWrite(10,LOW);
  digitalWrite(11,HIGH);
  digitalWrite(12,HIGH);
  digitalWrite(13,LOW);
  }
  

   void steepright()
{
  digitalWrite(10,HIGH);
  digitalWrite(11,LOW);
  digitalWrite(12,LOW);
  digitalWrite(13,HIGH);
  }

void loop() {
  // put your main code here, to run repeatedly:
  //black==1&&white==0
 int lir=digitalRead(5);
  int cir=digitalRead(6);
    int rir=digitalRead(7);
  
  Serial.println(lir);
  Serial.println(cir);
  Serial.println(rir);
   if((lir==0&&cir==1&&rir==0)||(lir==1&&cir==1&&rir==1))
   {  
    forward(); 
     
    }
   if(lir==1&&cir==1&&rir==0)
   {
    steepleft();
    } 
    if(lir==0&&cir==0&&rir==0)
   {
    forward();
    
    }
   if(lir==0&&cir==1&&rir==1)
   {
    steepright();
    } 
   if(lir==1&&cir==0&&rir==0)
   { 
    steepleft(); 
    }
   if(lir==0&&cir==0&&rir==1)
   { 
    steepright(); 
    }
    if(lir==1&&cir==0&&rir==1)
    {
      steepright();
      }
}

# Compact-size-PCB-for-Arduino-projects


![image](https://user-images.githubusercontent.com/19898602/164375703-a65be249-cfa0-44c1-a226-31efa8d600a2.png)


This is multipurpose PCB specially design for arduino projects so that we can connect multiple components at once with arduino
Those who ever worked with arduino they know the pain of connecting multiple components to the arduino for there projects. so here is the answer for you all.

Not only 2 or 3 you can connect 11 components at same time & on board 5V & 9V regulator,

cross polarity protection, power indication LED,

motor power selection provision (5V or 9V or 12V) manual provision for stepper motor microstepping setting.

Wide range of input supply (9V to 24V). This is my multipurpose PCB works with Arduino Nano, I have designed it in a way that you can run 2 Stepper motors, 2 DC motors, 2 Servo motors at same time and this is not it you can even connect BT module, rotary encoder, I2C device, potentiometer at same time.

This PCB is very much helpful in building any project and no need to worry about messy wire connections.

I design this PCB in Easyeda and order it from [JLCPCB.com](https://jlcpcb.com/IAT) they offer very affordable rate for quality PCB.

# Overview of PCB


![image](https://user-images.githubusercontent.com/19898602/164375763-e2d4c7e3-20bf-4157-b0ca-faaa43c52ab8.png)![image](https://user-images.githubusercontent.com/19898602/164375808-3edca2de-070f-4af5-986d-3dc743876d5a.png)

Here we first see the overview of PCB means what is this PCB capable of and which components you can connect to the PCB.

# List of the Components you can connect to the PCB

![image](https://user-images.githubusercontent.com/19898602/164375847-fd7101ee-0744-45ba-86f3-9df44bd28873.png)


2 DC motor ( 9V to 24V DC)


2 Potentiometer


2 Servo motors ( 5V to 9V DC)


1 Serial device (BT module, HMI, Communication module, RX, TX)


1 Encoder (2 interrupt pin & 1 PB pin)


1 I2C device (SCL/SDA Device, display, MPU6050 etc)


2 Stepper motors


# Special features of PCB 

![image](https://user-images.githubusercontent.com/19898602/164375902-aab9a1c4-c87c-43cd-9666-9f5abeebec2a.png)


Wide range of power input 9V to 24V DC


Cross polarity protection


DC motor voltage selection 9V or 12 V DC


Servo motor voltage selection 5V or 9V DC


Manual microstepping setting for stepper motor


Power indication LED


L298N IC for heavier DC motor


ON board 5V and 9V regulator no need to arrange different power sources


Header pins and screw terminals for easy connections


# PCB Design and PIN Details


![b](https://user-images.githubusercontent.com/19898602/164375961-2278b4e2-0209-49fa-a1ea-0588c8e57c32.JPG)![c](https://user-images.githubusercontent.com/19898602/164375975-362c836c-359e-436e-a462-8bcb1155d997.JPG)

![d](https://user-images.githubusercontent.com/19898602/164376092-7663a81f-8dc3-4922-9d52-6a5f5c74cd94.JPG)


I have design circuit and PCB ineasy EDA and ordered PCB from [JLCPCB.com](https://jlcpcb.com/IAT)




[JLCPCB.com](https://jlcpcb.com/IAT) are the world leader in PCB manufacturing there PCB production rates are very much affordable and they have world class PCB production unit results fast PCB production.

I have provided the link of circuit desgin so that you can modify it as per your need if you need to change any thing.

https://oshwlab.com/sharmaz747/multipurpose-pcb_copy_copy_copy


![image](https://user-images.githubusercontent.com/19898602/159014034-3c9a50c3-61c3-40d2-836d-9cadc2317d33.png)


SMT Assembly service of [JLCPCB.com](https://jlcpcb.com/IAT) is cherry on top now get your PCB fully assembled and save your time and money
Select components for your PCB from there Parts Library of 200k+ in-stock components
they are offering $27 valued New User coupons  & $24 SMT coupons every month
$8.00 setup fee, and $0.0017  per joint

Now no need to order components separately for you PCB and get free from stress of soldering them on PCB just try PCB SMT assembly service and get you PCB with components pre assembled and ready for the project


👉 Try PCBA service of [JLCPCB.com](https://jlcpcb.com/IAT) and save your time and money, get PCB ready for project, 200K+ components in library of [JLCPCB.com](https://jlcpcb.com/IAT) as well as 3rd party         parts to choose from. 
    Assembly will support 10M+ parts from Digikey, mouser
    
👉 $27 valued New User coupons 

👉 $24 SMT coupons every month


For more detials & offers please visit [JLCPCB.com](https://jlcpcb.com/IAT)


# Pin details of PCB

**DC MOTORS**

EN1, EN2 = D9


IN1 = D7


IN2 = D8


IN3 = D10


IN4 = D11


**POTENTIOMETER**



P1 = A6


P2 = A7


**SERVO MOTORS**



S1 = D5


S2 = D6


**SERIAL COM.**



DO = TX


D1 = RX


**ENCODER**



PB = D4


IN1 = D2


IN2 = D3


**I2C PORT**



SCL = A5


SDA = A4


**STEPPER MOTORS**



EN = D12


DIR1 = A0


STP1 = A1


DIR2 = A2


STP = A3


# Component Used


![image](https://user-images.githubusercontent.com/19898602/164376788-1b06e117-8d0a-4525-bc4e-676893774e8a.png)


# Demo Arduio proejct

Below is the code so that you can connect all the components with PCB and run them one by one with the help of encoder and 16x2 LCD display



```
#include <Wire.h>
#include "rgb_lcd.h"
rgb_lcd lcd;
#define CLK 3
#define DT 2
#define SW 4
#include <L298N.h>
#include <Servo.h>
#include "BasicStepperDriver.h"
#include "MultiDriver.h"
#include "SyncDriver.h"
#define MOTOR_STEPS 200
#define MOTOR_X_RPM 60
#define MOTOR_Y_RPM 60
#define DIR_X A0
#define STEP_X A1
#define DIR_Y A2
#define STEP_Y A3
#define MICROSTEPS 16
BasicStepperDriver stepperX(MOTOR_STEPS, DIR_X, STEP_X);
BasicStepperDriver stepperY(MOTOR_STEPS, DIR_Y, STEP_Y);
MultiDriver controller(stepperX, stepperY);

int counter = 0;
int currentStateCLK;
int lastStateCLK;
String currentDir = "";
unsigned long lastButtonPress = 0;
int screen = 0;
int state = 0;
int flag = 0;
const unsigned int IN1_A = 7;
const unsigned int IN2_A = 8;
const unsigned int IN1_B = 10;
const unsigned int IN2_B = 11;
const unsigned int EN = 9;
Servo myservo1;
Servo myservo2;
int pos = 0;

// Create one motor instance
L298N motor1(EN, IN1_A, IN2_A);
L298N motor2(EN, IN1_B, IN2_B);

void setup() {
  Serial.begin(9600);
  lcd.begin(16, 2);
  motor1.setSpeed(120);
  motor2.setSpeed(120);
  pinMode(CLK, INPUT);
  pinMode(DT, INPUT);
  pinMode(SW, INPUT_PULLUP);
  lastStateCLK = digitalRead(CLK);
  stepperX.begin(MOTOR_X_RPM, MICROSTEPS);
  stepperY.begin(MOTOR_Y_RPM, MICROSTEPS);

}

void loop() {
  if (state == 0) {
    lcd.setCursor(0, 0);
    lcd.print ("Press to start");
  }
  if (counter > 5) {
    counter = 0;
  }

  int btnState = digitalRead(SW);
  if (btnState == LOW) {
    if (millis() - lastButtonPress > 50) {
      Serial.println("Button pressed!");
      lcd.clear();
      state = 1;
      screen ++;
      flag = 0;
      Serial.println(screen);
    }

    lastButtonPress = millis();
  }

  if (state == 1) {
    currentStateCLK = digitalRead(CLK);
    if (currentStateCLK != lastStateCLK  && currentStateCLK == 1) {
      if (digitalRead(DT) != currentStateCLK) {
        counter --;
        currentDir = "CCW";
        lcd.clear();
      } else {
        counter ++;
        currentDir = "CW";
        lcd.clear();
      }

      Serial.print("Direction: ");
      Serial.print(currentDir);
      Serial.print(" | Counter: ");
      Serial.println(counter);
    }
    lastStateCLK = currentStateCLK;

    if (screen == 1) {
      Stop();
    }
    if (counter == 0) {
      DC_motor1();
      if (screen == 2) {
        lcd.setCursor(0, 1);
        lcd.print ("Running...");
        screen = 0;
        A ();
      }
    }

    if (counter == 1) {
      DC_motor2();
      if (screen == 2) {
        lcd.setCursor(0, 1);
        lcd.print ("Running...");
        screen = 0;
        B ();
      }
    }

    if (counter == 2) {
      Servo1();
      if (screen == 2) {
        lcd.setCursor(0, 1);
        lcd.print ("Running...");
        screen = 0;
        C ();
      }
    }
    if (counter == 3) {
      Servo2();
      if (screen == 2) {
        lcd.setCursor(0, 1);
        lcd.print ("Running...");
        screen = 0;
        D ();
      }
    }

    if (counter == 4) {
      Stepper1();
      if (screen == 2) {
        lcd.setCursor(0, 1);
        lcd.print ("Running...");
        screen = 0;
        flag = 1;
      }
    }
    if (counter == 5) {
      Stepper2();
      if (screen == 2) {
        lcd.setCursor(0, 1);
        lcd.print ("Running...");
        screen = 0;
        flag = 2;
      }
    }
  }

  delay(5);
}


void DC_motor1() {

  lcd.setCursor(0, 0);
  lcd.print ("DC MOTOR 1");
}

void DC_motor2() {

  lcd.setCursor(0, 0);
  lcd.print ("DC MOTOR 2");
}

void Servo1() {

  lcd.setCursor(0, 0);
  lcd.print ("Servo 1");
}

void Servo2() {

  lcd.setCursor(0, 0);
  lcd.print ("Servo 2");
}

void Stepper1() {

  lcd.setCursor(0, 0);
  lcd.print ("Stepper 1");
}

void Stepper2() {

  lcd.setCursor(0, 0);
  lcd.print ("Stepper 2");
}



void A () {
  motor1.forward();
}

void B () {
  motor2.forward();
}

void Stop() {
  motor1.stop();
  motor2.stop();
  myservo1.detach();
  myservo2.detach();
  controller.rotate(0, 0);
}


void C () {
  myservo1.attach(9);

  for (pos = 0; pos <= 180; pos += 1) {
    // in steps of 1 degree
    myservo1.write(pos);
    delay(15);
  }
  for (pos = 180; pos >= 0; pos -= 1) {
    myservo1.write(pos);
    delay(15);

  }
}


void D () {
  myservo2.attach(10);
  for (pos = 0; pos <= 180; pos += 1) {
    // in steps of 1 degree
    myservo2.write(pos);
    delay(15);
  }
  for (pos = 180; pos >= 0; pos -= 1) {
    myservo2.write(pos);
    delay(15);

  }
}

void E() {
  controller.rotate(1, 0);
}

void X() {
  controller.rotate(0, 1);
}

```





![MVI_0011_1](https://user-images.githubusercontent.com/19898602/164378235-e78dabd3-d77d-404e-bead-084f5cf1036a.gif)






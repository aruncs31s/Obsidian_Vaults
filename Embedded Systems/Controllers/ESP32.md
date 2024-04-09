

# ESP32
## Contents
- [Interfacings](#interfacings)
	1. [LDR](#ldr%20interfacing)
	2. [PIR](#pir%20interfacing)
	3. [Servo Motor](#servo%20motor)
	4. [UltraSonic](#ultrasonic%20sensor%20interfacing)
- [Multi Threading](#milti%20threading)


### Interfacings

- [LDR](#ldr%20interfacing)
- [PIR](#pir%20interfacing)
- [Servo Motor](#servo%20motor)
- [UltraSonic](#ultrasonic%20sensor%20interfacing)
#### LDR Interfacing

```c
const int LDR_PIN = 36;

void setup() {
   Serial.begin(9600);
   analogReadResolution(10); //default is 12. Can be set between 9-12.
}
void loop() {
   float LDR_Voltage = ((float)LDR_Reading*3.3/1023);
   Serial.print("Reading: ");Serial.print(LDR_Reading); Serial.print("\t");Serial.print("Voltage: ");Serial.println(LDR_Voltage);
}

```


#### PIR Interfacing
[Source](https://www.electronicwings.com/esp32/pir-sensor-interfacing-with-esp32)
```c
  Serial.println("Waiting For Power On Warm Up");
  delay(20000); /* Power On Warm Up Delay */
  Serial.println("Ready!");
}
int sensor_output;
void loop() {
  
  sensor_output = digitalRead(PIR_SENSOR_OUTPUT_PIN);
  Serial.println(sensor_output + "\n"); 
  delay(100);
  // if( sensor_output == LOW )
  // {
  //   if( warm_up == 1 )
  //    {
  //     Serial.print("Warming Up\n\n");
  //     warm_up = 0;
  //     delay(2000);
  //   }
  //   // Serial.print("No object in sight\n\n");
  //   delay(1000);
  // }
  // else
  // {
  //   // Serial.print("Object detected\n\n");   
  //   warm_up = 1;
  //   delay(100);
  // } 
}
```

---

#### Servo Motor Interfacing

```c
/*********
  Rui Santos
  Complete project details at https://RandomNerdTutorials.com/
  Written by BARRAGAN and modified by Scott Fitzgerald
*********/

#include <Servo.h>

static const int servoPin = 13;

Servo servo1;

void setup() {
  Serial.begin(115200);
  servo1.attach(servoPin);
}

void loop() {
  for(int posDegrees = 0; posDegrees <= 180; posDegrees++) {
    servo1.write(posDegrees);
    Serial.println(posDegrees);
    delay(20);
  }

```


#### Servo Motor Interfacing 2

#TestCode
[Source](https://chat.openai.com/)

```c
#include <ESP32Servo.h>

// Define the GPIO pin connected to the servo
const int servoPin = 2;

// Create a Servo object
Servo myservo;

void setup() {
  Serial.begin(9600);

  // Attach the servo to the GPIO pin
  myservo.attach(servoPin);
}

void loop() {
  // Sweep the servo back and forth
  for (int angle = 0; angle <= 180; angle += 1) {
    myservo.write(angle);
    delay(15);
  }
  for (int angle = 180; angle >= 0; angle -= 1) {
    myservo.write(angle);
    delay(15);
  }
}
```



#### Ultrasonic Sensor Interfacing
[Source](https://randomnerdtutorials.com/esp32-hc-sr04-ultrasonic-arduino/)

- $distance\ to\ an\ object = ((speed\ of\ sound\ in\ the\ air)*time)/2$

![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2021/06/ESP32-Ultrasonic-Sensor-Wiring-Fritzing-Diagram.png?w=846&quality=100&strip=all&ssl=1)
#exampleCode 
[Source](https://randomnerdtutorials.com/esp32-hc-sr04-ultrasonic-arduino/)
```c
/*********
  Rui Santos
  Complete project details at https://RandomNerdTutorials.com/esp32-hc-sr04-ultrasonic-arduino/
  
  Permission is hereby granted, free of charge, to any person obtaining a copy
  of this software and associated documentation files.
  
  The above copyright notice and this permission notice shall be included in all
  copies or substantial portions of the Software.
*********/

const int trigPin = 5;
const int echoPin = 18;

//define sound speed in cm/uS
#define SOUND_SPEED 0.034
#define CM_TO_INCH 0.393701

long duration;
float distanceCm;
float distanceInch;

void setup() {
  Serial.begin(115200); // Starts the serial communication
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
  pinMode(echoPin, INPUT); // Sets the echoPin as an Input
}

void loop() {
  // Clears the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate the distance
  distanceCm = duration * SOUND_SPEED/2;
  
  // Convert to inches
  distanceInch = distanceCm * CM_TO_INCH;
  
  // Prints the distance in the Serial Monitor
  Serial.print("Distance (cm): ");
  Serial.println(distanceCm);
  Serial.print("Distance (inch): ");
  Serial.println(distanceInch);
  
  delay(1000);
}
```

#modifiedCode 

```c
//Defiining Interfacing Pins
const int trigPin = 15;
const int echoPin = 2;

void setup(){

}



```

---


#### Multi Threding
```c
/*
Source : https://randomnerdtutorials.com/esp32-dual-core-arduino-ide/ */
*/
/*********
  Rui Santos
  Complete project details at https://randomnerdtutorials.com  
*********/

TaskHandle_t solar_tracking_id;
TaskHandle_t energy_managment_id;

// LED pins
const int led1 = 2;
const int led2 = 4;
//
void setup() {
  Serial.begin(9600); 
  // pinMode(led1, OUTPUT);
  // pinMode(led2, OUTPUT);

  //create a task that will be executed in the Task1code() function, with priority 1 and executed on core 0
  xTaskCreatePinnedToCore(
                    Solar_Managment,   /* Task function. */
                    "Task1",     /* name of task. */
                    10000,       /* Stack size of task */
                    NULL,        /* parameter of the task */
                    1,           /* priority of the task */
                    &solar_tracking_id,      /* Task handle to keep track of created task */
                    0);          /* pin task to core 0 */                  
  delay(500); 

  //create a task that will be executed in the Task2code() function, with priority 1 and executed on core 1
  xTaskCreatePinnedToCore(
                    Energy_Managment,   /* Task function. */
                    "Task2",     /* name of task. */
                    10000,       /* Stack size of task */
                    NULL,        /* parameter of the task */
                    1,           /* priority of the task */
                    &energy_managment_id,      /* Task handle to keep track of created task */
                    1);          /* pin task to core 1 */
    delay(500); 
}

//Task1code: blinks an LED every 1000 ms
void Solar_Managment( void * pvParameters ){
  Serial.print("Task1 running on core ");
  Serial.println(xPortGetCoreID());

  for(;;){
    digitalWrite(led1, HIGH);
    delay(1000);
    digitalWrite(led1, LOW);
    delay(1000);
  } 
}

//Task2code: blinks an LED every 700 ms
void Energy_Managment( void * pvParameters ){
  
  
  Serial.print("Task2 running on core ");
  Serial.println(xPortGetCoreID());

  // for(;;){
  //   digitalWrite(led2, HIGH);
  //   delay(700);
  //   digitalWrite(led2, LOW);
  //   delay(700);
  // }
}

void loop() {
  
}


```

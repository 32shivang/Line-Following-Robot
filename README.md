Line follower is an autonomous robot which follows either black line in white are or white line in black area. Robot must be able to detect particular line and keep following it.

For special situations such as cross overs where robot can have more than one path which can be followed, predefined path must be followed by the robot.

Input: Read the white/black on the floor and condition the input signal(s) for transmission into the microcontroller in a way that questions can be asked and decisions made.

Process: Based on the inputs received, microcontroller decide what change (if any) needs to be made to the robots speed and direction. Convert the results of any decisions made into something that can be sent to motor speed control and/or steering.

Output: Send the old or the newly adjusted control signals to speed and/or steering devices.

Materials used
☞Robo Car
☞Arduino Uno
☞Line following sensor

Sample Code:

#define REF 200

const int MotR_A = 3; // DC Motor1 Pole_A

const int MotR_B = 5; // DC Motor1 Pole_B

const int MotL_A = 6; // DC Motor2 Pole_A

const int MotL_B = 9; // DC Motor2 Pole_B

unsigned int Flag1,Flag2,Flag3,Flag4,Val;

void setup()

{

Serial.begin(9600);

pinMode(MotR_A, OUTPUT);

pinMode(MotR_B, OUTPUT);

pinMode(MotL_A, OUTPUT);

pinMode(MotL_B, OUTPUT);

}

void loop()

{

int sen1 = analogRead(A0);

int sen2 = analogRead(A1);

int sen3 = analogRead(A2);

int sen4 = analogRead(A3);

if (sen1>REF)

{ Flag1 = 1; }

else

{ Flag1 = 0; }

if (sen2>REF)

{ Flag2 = 1; }

else

{ Flag2 = 0; }

if (sen3>REF)

{ Flag3 = 1; }

else

{ Flag3 = 0; }

if (sen4>REF)
{ Flag4 = 1; }
else
{ Flag4 = 0; }

Val = (Flag1 | (Flag2<<1) | (Flag3<<2) | (Flag4<<3) );

Serial.print(Val);

Serial.println();

switch (Val)

{

case 0:

Robo_Right();

break;

case 1:

Robo_Left();

break;

case 3:

Robo_Left();

break;

case 6:

Robo_Front();

break;

case 7:

Robo_Left();

break;

case 8:

Robo_Right();

break;

case 12:

Robo_Right();

break;

case 14:

Robo_Right();

break;

case 15:

Robo_Front();

break;

default:

break;

}
}

void Robo_Front()

{

digitalWrite(MotR_A, LOW);

digitalWrite(MotR_B, HIGH);

digitalWrite(MotL_B, LOW);

digitalWrite(MotL_A, HIGH);

}
void Robo_Back()

{

digitalWrite(MotR_A, HIGH);

digitalWrite(MotR_B, LOW);

digitalWrite(MotL_B, HIGH);

digitalWrite(MotL_A, LOW);

}

void Robo_Right()

{

digitalWrite(MotR_A, HIGH);

digitalWrite(MotR_B, LOW);

digitalWrite(MotL_B, LOW);

digitalWrite(MotL_A, HIGH);

}

void Robo_Left()

{

digitalWrite(MotR_A, LOW);

digitalWrite(MotR_B, HIGH);

digitalWrite(MotL_B, HIGH);

digitalWrite(MotL_A, LOW);

}

void Robo_Stop()

{

digitalWrite(MotR_A, LOW);

digitalWrite(MotR_B, LOW);

digitalWrite(MotL_B, LOW);

digitalWrite(MotL_A, LOW);

}

Advantages of Line follower robot

☞Robot movement is automatic.

☞Used for long distance applications.

☞Used in home, industrial automation and Health Care.

☞Cost effective.

☞Simplicity of building.

Disadvantages of Line follower robot

☞Line follower robot follows a black line about 1 or 2 inches in width on a white surface.

☞Line tracing robots are simple robots with an additional sensors placed on them.

☞It always needs a path to run either white or black since the IR rays should reflect from the particular path.

☞Slow speed and instability on different line thickness or hard angles.

Applications of Line follower robot

☞Guidance system for industrial robots moving on shop floor etc.

☞Healthcare applications

☞Industrial applications.

☞Home applications.

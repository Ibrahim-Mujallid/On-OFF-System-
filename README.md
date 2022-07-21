# On-OFF-System- 
Objective : design On off system using relay and transistor and pushbutton and other electronics components with arduino 
used components: - Arduino Uno R3 - (1K) ohm resistor - NPN transistor (BJT) - Relay SPDT - diode - pushbutton - Blue LED - 9V battery 
used code : 
const int button = 2, relay = 10;
int lastButtonState = HIGH, buttonState, relayState = LOW;
bool pressed = false;
unsigned long previousTime = 0;

void setup(){
    pinMode(button, INPUT_PULLUP);                          
    pinMode(relay, relayState);
    digitalWrite(relay, relayState);
}

void loop(){
    buttonState = digitalRead(button);
    if(lastButtonState != buttonState){
        pressed = true;
        previousTime = millis();
    }
    if(pressed){
        if(millis() - previousTime >= DEBOUNCE){
            pressed = false;
            if(buttonState == LOW){    
                digitalWrite(relay, (relayState = !relayState));   
            }
        }
    }
    lastButtonState = buttonState;
}

// Please long press B to pause/resume


#include <Keypad.h>
const byte ROWS = 4;
const byte COLS = 4;

char key;
char tensh;
char onesh;
char tensm;
char onesm;
char tenss;
char oness;
int a = 0;
int v = 0;
int fd = 0;

int ic = 0;

char ckey;
char ctensh;
char conesh;
char ctensm;
char conesm;
char ctenss;
char coness;

int cseconds;
int cminutes;
int chours;

int sseconds;
int sminutes;

int ii=0;

char hexaKeys[ROWS][COLS] = 
{
  {'1', '2', '3', 'A'},
  {'4', '5', '6', 'B'},
  {'7', '8', '9', 'C'},
  {'*', '0', '#', 'D'}
};

char set = hexaKeys[3][0];
char pause = hexaKeys[3][2];
char homeKey = hexaKeys[3][3];

byte rowPins[ROWS] = {A0, A1, 11, 10};
byte colPins[COLS] = {9, 8, 7, 6};
 
Keypad customKeypad = Keypad(makeKeymap(hexaKeys), rowPins, colPins, ROWS, COLS);
 
//________________________________________________________

#include <LiquidCrystal.h>

LiquidCrystal LCD(5, 4, 3, 2, A4, A5);

int seconds;
int minutes;
int hours;
int i = 0;

//_________________________________________________________
int keypadConvertor(char z)
{
  int l = z;
  int m = l-48;
  if(m>=0 && m < 10) return m;
  else return 0;
}

int keypadSet(char g)
{
  int f = 1; int e = 0;
  if(g == hexaKeys[0][3]){return f;}
  else{return e;}  
}

//_________________________________________________________
void myTimer()
{
  LCD.clear();
  if(i == 0)
  { 
    LCD.setCursor(0,0);
    LCD.print("Set timer");
    
    delay(1000);
    
    beginning:
    
    LCD.clear();  
    
    LCD.setCursor(0,0);
    LCD.print("Enter minutes     ");
    while(a<2)
    {
      char key = customKeypad.getKey();
      if (key!=NO_KEY) 
      {
        LCD.setCursor(a,1);
        LCD.print(key);
        if(a==0)
        {
          tensm=key;
          Serial.print(tensm);
        }
        if(a==1)
        {
          onesm=key;
          Serial.println(onesm);
        }       
        
        a++;
      }
    }
    
    int t2 = keypadConvertor(tensm);
    int o2 = keypadConvertor(onesm);
    
    minutes = t2*10 + o2;
    a=0;
    
    Serial.println(minutes);
    
    if(minutes >= 10)
    { 
      LCD.setCursor(0,1);
      if(minutes < 100)
      {
        LCD.print(minutes);
      }
    }
    else if(minutes < 10)
    {
      LCD.setCursor(0,1);
      LCD.print(0);
      LCD.setCursor(1,1);
      LCD.print(minutes);
    }
    LCD.setCursor(2,1); 
    LCD.print(":");
    
    delay(1000);
    
    
    
    
    LCD.setCursor(0,0);
    LCD.print("Enter seconds    ");
    while(a<2)
    {
      char key = customKeypad.getKey();
      if (key!=NO_KEY) 
      {
        LCD.setCursor((a+3),1);
        LCD.print(key);
        if(a==0)
        {
          tenss=key;
          Serial.print(tenss);
        }
        if(a==1)
        {
          oness=key;
          Serial.println(oness);
        }       
        
        a++;
      }
    }
    
    int t3 = keypadConvertor(tenss);
    int o3 = keypadConvertor(oness);
    
    seconds = t3*10 + o3;
    a=0;

    Serial.println(seconds);
    
    
    LCD.clear();
    LCD.setCursor(0,0);
    LCD.print("Set the timer?");
    LCD.setCursor(0,1);
    LCD.print("yes: * || no: #");  
    
    int c=0;
    
    while(c<1)
    {
      char check = customKeypad.getKey();
      
      if(check != NO_KEY)
      {
        if(check==set) goto time;
        else goto beginning;
      }
    }
    
    
    
    time:
    
 
    LCD.clear();
  
    LCD.setCursor(0,0);
    LCD.print("LCD Timer          ");
    delay(500);
    LCD.setCursor(0,0);
    LCD.print("Long press #         ");
    LCD.setCursor(0,1);
    LCD.print("to PAUSE      ");
    delay(2000);
    LCD.clear();
    LCD.setCursor(0,0);
    LCD.print("LCD Timer          ");
    
    
    
    if(seconds >= 10)
    { 
      if(seconds < 60)
      {
        LCD.setCursor(3,1);      
        LCD.print(seconds);
      }      
    }
    else if(seconds < 10)
    {
      if(seconds > 0)
      {
        LCD.setCursor(3,1);
        LCD.print(0);
        LCD.setCursor(4,1);
        LCD.print(seconds);
      }
      else if(seconds == 0)
      { 
        LCD.setCursor(3,1);
        LCD.print(0);
        LCD.setCursor(4,1);
        LCD.print(0);        
      }
    }
    
    if(seconds > 61)
    {
      Serial.print("Error");
      LCD.setCursor(0,1);
      LCD.print("Error            ");
    }

       
    i++; 
  }
  
  
  timer:
  
  LCD.setCursor(0,0);
  LCD.print("LCD Timer          ");
  
  LCD.setCursor(7,1);
  LCD.print("Pause:#");
  
 
  if(seconds >= 10)
  {
    LCD.setCursor(3,1);
    LCD.print(seconds);
    seconds--;
  }

  else if(seconds < 10)
  { 
    if(seconds > 0)
    {
      LCD.setCursor(3,1);
      LCD.print(0);
      LCD.setCursor(4,1);
      LCD.print(seconds);
      seconds--;
    }
    else if(seconds == 0)
    { 
      seconds = seconds + 60; 
      minutes--;
      LCD.setCursor(3,1);
      LCD.print(6);
      LCD.setCursor(4,1);
      LCD.print(0);
      seconds--;     
    }
  }
  
  LCD.setCursor(2,1);
  LCD.print(":");
  
  if(minutes >= 10)
  { 
    LCD.setCursor(0,1);
    LCD.print(minutes);
  }

  else if(minutes < 10)
  {
    LCD.setCursor(0,1);
    LCD.print(0);
    LCD.setCursor(1,1);
    LCD.print(minutes);
  }
  
  if(minutes==0 && seconds==0)
  {
    while(fd<1)
    {
      LCD.setCursor(0,1);
      LCD.print(0);
      LCD.setCursor(1,1);
      LCD.print(0);
      LCD.setCursor(2,1);
      LCD.print(":");
      LCD.setCursor(3,1);
      LCD.print(0);
      LCD.setCursor(4,1);
      LCD.print(0);
    }
  }

  delay(1000);
  
  char check = customKeypad.getKey();
  if(check != NO_KEY)
  {
    if(check==pause) goto paused;
    if(check==homeKey) goto exit;
    else goto timer;
  }
  else goto timer;
  
  while(v<1)
  {
    paused:
    LCD.setCursor(0,0);
    LCD.print("# to resume       ");
    LCD.setCursor(7,1);
    LCD.print("           ");
    char check = customKeypad.getKey();
    
    if(check != NO_KEY)
    {
      if(check==pause) goto timer;
      if(check==homeKey) goto exit;
      else goto paused;
    }
  }
  exit:
  Serial.print("exit");
}
//_________________________________________________________

void myClock()
{
  LCD.clear();
  if(ic == 0)
  { 
    LCD.setCursor(0,0);
    LCD.print("Enter time");
    
    delay(1000);
    
    beginning:
    
    LCD.clear();
    
    LCD.setCursor(0,0);
    LCD.print("Enter hours      ");
    
    while(a<2)
    {
      char key = customKeypad.getKey();
      if (key!=NO_KEY) 
      {
        LCD.setCursor(a,1);
        LCD.print(key);
        if(a==0)
        {
          tensh=key;
          Serial.print(tensh);
        }
        if(a==1)
        {
          onesh=key;
          Serial.println(onesh);
        }       
        
        a++;
      }
    }
    
    int t1 = keypadConvertor(tensh);
    int o1 = keypadConvertor(onesh);
    
    hours = t1*10 + o1;   
    a=0;
    
    Serial.println(hours);
    
    if(hours >= 10)
    { 
      LCD.setCursor(0,1);
      if(hours < 24)
      {
        LCD.print(hours);
      }
      else if(hours == 24)
      {
        LCD.print(0);
        LCD.setCursor(1,1);
        LCD.print(0);
      }
    }
    else if(hours < 10)
    {
      LCD.setCursor(0,1);
      LCD.print(0);
      LCD.setCursor(1,1);
      LCD.print(hours);
    }
    LCD.setCursor(2,1);
    LCD.print(":");
      
    if(hours > 25)
    {
      Serial.print("Error");
      LCD.setCursor(0,1);
      LCD.print("Error            ");
    }
    delay(1000);
        
    
    
    LCD.setCursor(0,0);
    LCD.print("Enter minutes     ");
    while(a<2)
    {
      char key = customKeypad.getKey();
      if (key!=NO_KEY) 
      {
        LCD.setCursor((a+3),1);
        LCD.print(key);
        if(a==0)
        {
          tensm=key;
          Serial.print(tensm);
        }
        if(a==1)
        {
          onesm=key;
          Serial.println(onesm);
        }       
        
        a++;
      }
    }
    
    int t2 = keypadConvertor(tensm);
    int o2 = keypadConvertor(onesm);
    
    minutes = t2*10 + o2;
    a=0;
    
    Serial.println(minutes);
    
    if(minutes >= 10)
    { 
      LCD.setCursor(3,1);
      if(minutes < 60)
      {
        LCD.print(minutes);
      }
      else if(minutes == 60)
      {
        LCD.print(0);
        LCD.setCursor(4,1);
        LCD.print(0);
      }
    }
    else if(minutes < 10)
    {
      LCD.setCursor(3,1);
      LCD.print(0);
      LCD.setCursor(4,1);
      LCD.print(minutes);
    }
    LCD.setCursor(5,1); 
    LCD.print(":");
    
    if(minutes > 61)
    {
      Serial.print("Error");
      LCD.setCursor(0,1);
      LCD.print("Error            ");
    }    
    delay(1000);
    
        
    
    LCD.setCursor(0,0);
    LCD.print("Enter seconds    ");
    while(a<2)
    {
      char key = customKeypad.getKey();
      if (key!=NO_KEY) 
      {
        LCD.setCursor((a+6),1);
        LCD.print(key);
        if(a==0)
        {
          tenss=key;
          Serial.print(tenss);
        }
        if(a==1)
        {
          oness=key;
          Serial.println(oness);
        }       
        
        a++;
      }
    }
    
    int t3 = keypadConvertor(tenss);
    int o3 = keypadConvertor(oness);
    
    seconds = t3*10 + o3;
    a=0;

    Serial.println(seconds);
    
    
    LCD.clear();
    LCD.setCursor(0,0);
    LCD.print("Set the time?");
    LCD.setCursor(0,1);
    LCD.print("yes: * || no: #");  
    
    int c=0;
    
    while(c<1)
    {
      char check = customKeypad.getKey();
      
      if(check != NO_KEY)
      {
        if(check==set) goto time;
        else goto beginning;
      }
    }
    
    time:
    
    LCD.clear();
  
    LCD.setCursor(0,0);
    LCD.print("LCD Clock");
    
    if(seconds >= 10)
    { 
      if(seconds < 60)
      {
        LCD.setCursor(6,1);      
        LCD.print(seconds);
      }
      else if(seconds == 60)
      { 
        LCD.setCursor(6,1);
        LCD.print(0);
        LCD.setCursor(7,1);
        LCD.print(0);        
      }
    }
    else if(seconds < 10)
    { 
      LCD.setCursor(6,1);
      LCD.print(0);
      LCD.setCursor(7,1);
      LCD.print(seconds);
    }
    
    if(seconds > 61)
    {
      Serial.print("Error");
      LCD.setCursor(0,1);
      LCD.print("Error            ");
    }

       
    ic++; 
  }
  
  clocker:
    
  if(seconds >= 10)
  { 
    if(seconds < 60)
    {
      LCD.setCursor(6,1);
      LCD.print(seconds);
      seconds++;
    }
    else if(seconds == 60)
    { 
      minutes++;
      LCD.setCursor(6,1);
      LCD.print(0);
      LCD.setCursor(7,1);
      LCD.print(0);
      seconds++;
      seconds = seconds - 60; 
    }
  }
  else if(seconds < 10)
  { 
    LCD.setCursor(6,1);
    LCD.print(0);
    LCD.setCursor(7,1);
    LCD.print(seconds);
    seconds++;
  }
  
  LCD.setCursor(5,1); 
  LCD.print(":");
  LCD.setCursor(2,1);
  LCD.print(":");
  
  if(minutes >= 10)
  { 
    LCD.setCursor(3,1);
    if(minutes < 60)
    {
      LCD.print(minutes);
    }
    else if(minutes == 60)
    {
      hours++;
      LCD.print(0);
      LCD.setCursor(4,1);
      LCD.print(0);
      minutes = minutes - 60;
    }
  }
  else if(minutes < 10)
  {
    LCD.setCursor(3,1);
    LCD.print(0);
    LCD.setCursor(4,1);
    LCD.print(minutes);
  }
  
  if(hours >= 10)
  { 
    LCD.setCursor(0,1);
    if(hours < 24)
    {
      LCD.print(hours);
    }
    else if(hours == 24)
    {
      LCD.print(0);
      LCD.setCursor(1,1);
      LCD.print(0);
      hours = hours - 24;
    }
  }
  else if(hours < 10)
  {
    LCD.setCursor(0,1);
    LCD.print(0);
    LCD.setCursor(1,1);
    LCD.print(hours);
  }
 
  delay(1000); 
  
  char check = customKeypad.getKey();
  
  if(check != NO_KEY)
  {
    if(check==homeKey) goto exit;
    else goto clocker;
  }
  
  goto clocker;
  
  exit:
  Serial.print("exit");
}
//_________________________________________________________
void myStopwatch()
{
  LCD.clear();
  if(i == 0)
  { 
    LCD.setCursor(0,0);
    LCD.print("Stopwatch");
    LCD.setCursor(0,1);
    LCD.print("Long press #");
    
    delay(1500);
    
    beginning:
    
    sseconds = 0; sminutes = 0;
           
    LCD.clear();
    LCD.setCursor(0,0);
    LCD.print("Start Stopwatch?");
    LCD.setCursor(0,1);
    LCD.print("yes: * || no: #");  
    
    int c=0;
    
    while(c<1)
    {
      char check = customKeypad.getKey();
      
      if(check != NO_KEY)
      {
        if(check==set) goto time;
        else goto beginning;
      }
    }
    
    
    time:

       
    i++; 
  }
  
  
  stopwatch:
  
  LCD.setCursor(0,0);
  LCD.print("LCD Stopwatch          ");
  
  LCD.setCursor(5,1);
  LCD.print("  Pause:#      ");
  
 
  if(sseconds >= 10)
  { 
    if(sseconds < 60)
    {
      LCD.setCursor(3,1);
      LCD.print(sseconds);
      sseconds++;
    }
    else if(sseconds == 60)
    { 
      sminutes++;
      LCD.setCursor(3,1);
      LCD.print(0);
      LCD.setCursor(4,1);
      LCD.print(0);
      sseconds++;
      sseconds = sseconds - 60; 
    }
  }
  else if(sseconds < 10)
  { 
    LCD.setCursor(3,1);
    LCD.print(0);
    LCD.setCursor(4,1);
    LCD.print(sseconds);
    sseconds++;
  }
  
  LCD.setCursor(2,1);
  LCD.print(":");
  
  if(sminutes >= 10)
  { 
    LCD.setCursor(0,1);
    LCD.print(sminutes);
  }

  else if(sminutes < 10)
  {
    LCD.setCursor(0,1);
    LCD.print(0);
    LCD.setCursor(1,1);
    LCD.print(sminutes);
  }
  
  if(sminutes >= 10)
  { 
    LCD.setCursor(0,1);
    if(sminutes < 60)
    {
      LCD.setCursor(0,1);
      LCD.print(sminutes);
    }
  }
  else if(sminutes < 10)
  {
    LCD.setCursor(0,1);
    LCD.print(0);
    LCD.setCursor(1,1);
    LCD.print(sminutes);
  }
 
  delay(1000);
  
  char check = customKeypad.getKey();
  if(check != NO_KEY)
  {
    if(check==pause) goto paused;
    if(check==homeKey) goto exit;
    else goto stopwatch;
  }
  else goto stopwatch;
  
  while(v<1)
  {
    paused:
    LCD.setCursor(0,0);
    LCD.print("# to resume       ");
    LCD.setCursor(7,1);
    LCD.print("           ");
    char check = customKeypad.getKey();
    
    if(check != NO_KEY)
    {
      if(check==pause) goto stopwatch;
      if(check==homeKey) goto exit;
      else goto paused;
    }
  }
  exit:
  Serial.print("exit");
  
}
//_________________________________________________________


void setup()
{
  LCD.begin(16, 2);
  Serial.begin(9600);
}

char timerKey = hexaKeys[0][3];
char clockKey = hexaKeys[1][3];
char stopwatchKey = hexaKeys[2][3];
//_________________________________________________________

void loop()
{
  int v = 0;  
  while(v<1)
  {
    homeScreen:
    LCD.setCursor(0,0);
    LCD.print("A:timer B:clock");
    LCD.setCursor(0,1);
    LCD.print("C:stopwatch   ");
    
    char service = customKeypad.getKey();
    
    if(service != NO_KEY)
    {
      if(service==timerKey) myTimer();
      if(service==clockKey) myClock();
      if(service==stopwatchKey) myStopwatch();
      if(service==homeKey) goto homeScreen;      
      else goto homeScreen;
    }
  }
    
}

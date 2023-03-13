while(1==1):
  SpeedLeft = (getVar("$JoystickY1")*-100) - (getVar("$JoystickX1")*-100);
  SpeedRight = (getVar("$JoystickY1")*-100) + (getVar("$JoystickX1")*-100);
  
  if(SpeedLeft > 100): 
    PWM.Set(D5, 100);
    SpeedLeft = 100;
    
  if(SpeedLeft > 17): 
    Digital.Set(D6, 1);
    Digital.Set(D7, 0);
    PWM.Set(D5, int(SpeedLeft));
    
 
  if(-17 < SpeedLeft < 17):
    Digital.Set(D6, 0);
    Digital.Set(D7, 0);
  
  
  if(SpeedLeft < -100):
    PWM.Set(D5, 100);
    SpeedLeft = -100;
    
 
  if(SpeedLeft <= -17):
    Digital.Set(D6, 0);
    Digital.Set(D7, 1);
    PWM.Set(D5, int(SpeedLeft*-1));
    
 
  if(SpeedRight > 100): 
    PWM.Set(D5, 100);
    SpeedRight = 100;  
  if(SpeedRight > 17): 
    Digital.Set(D8, 1);
    Digital.Set(D9, 0);
    PWM.Set(D10, int(SpeedRight));
    
  
  if(-17 < SpeedRight < 17):
    Digital.Set(D8, 0);
    Digital.Set(D9, 0);
  
  
  if(SpeedRight < -100):
    PWM.Set(D5, 100);
    SpeedRight = -100;  
  if(SpeedRight <= -17):
    Digital.Set(D8, 0);
    Digital.Set(D9, 1);
    PWM.Set(D10, int(SpeedRight*-1));
  
 
  if(getVar("$JoystickX1")*-100 < -55):
    SpeedRight = 0;
    PWM.Set(D10, 0);
    
  if(getVar("$JoystickX1")*-100 > 55):
    SpeedLeft = 0; 
    PWM.Set(D5, 0);
    
    
    
  print(SpeedLeft, SpeedRight);
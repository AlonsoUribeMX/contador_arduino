# contador_arduino
contador de objetos o personas , con sensor ir 
#include <LiquidCrystal_I2C.h> 
#include<Wire.h>

LiquidCrystal_I2C lcd(0x3F,16,2);
const int LED = 13;
int SENSOR = 2;
int valor=0;
int numero=0;
int auxnumero=0;

void setup(){
  
  pinMode(LED, OUTPUT);
  pinMode(SENSOR, INPUT);  
   lcd.init();
  lcd.backlight();          // Activar luz de fondo 
  lcd.clear();              // Borrar LCD
  lcd.setCursor(2,0);       // coordenadas LCD (x,y)
  lcd.print("**** CUH ****");   // Mensaje de inicio
    lcd.setCursor(1,1);       // coordenadas LCD 
  lcd.print("ING. SISTEMAS");   // Mensaje de inicio
  delay (3000);
  lcd.clear(); 
  lcd.setCursor(0,0);       // coordenadas LCD 
  lcd.print("CONTADOR DIGITAL");
  lcd.setCursor(2,1);
  lcd.print("GRUPO 17");   
  delay (2000);
  lcd.clear();
  //lcd.setCursor(2,1);       
  //lcd.print("PERSONA #");  
  
  delay(1000);
}

void loop(){
  valor = digitalRead(SENSOR);
  lcd.setCursor(2,0);       // coordenadas LCD 
  lcd.print("**** CUH ****"); 
  lcd.setCursor(2,1);
  lcd.print("PERSONA #");
  lcd.setCursor(12, 1);
  lcd.print(numero);
  auxnumero=0;
  while(valor<1){
  valor = digitalRead(SENSOR);
  if (auxnumero==0){
    numero++;
    auxnumero=1;}
    }
  digitalWrite(LED, !auxnumero);//!auxnumero

  delay(300);
}

#include "TinyGPS++.h"
#include "SoftwareSerial.h"

SoftwareSerial serial_connection(11, 10);
TinyGPSPlus gps;

void setup()
{
  Serial.begin(9600);
  serial_connection.beign(9600);
  Serial.println("GPS Start");

}

void loop()
{
while (serial_connection.avaiable());
{
gps.encode(serial_connection.read());
}




if(gps.location.isUpdated());
{
Serial.beign(9600);
Serial.print("\r");

delay(1000);
Serial.print(AT+CMGF=1\r");
delay(1000);
Serial.print(AT+CMGS=\"+966555390020\ "\r\");
delay(1000);
Serial.print("I am lost!");
Serial.print("www.google.com.ph/maps/place/");
Serial.print(gps.location.lat(), 6);
Serial.print(",");
Serial.print(gps.location.lng(), 6);
Serial.print("\r");
delay(1000);
Serial.print((char)26);
delay(1000);
Serial.write(0x1A);
Serial.write(0x0D);
Serial.write(0x0A);
delay(1000);

}


}
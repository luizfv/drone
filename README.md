int IN1 = 4;
int IN2 = 5;
int IN3 = 6;
int IN4 = 7;
int velocidadeA = 3;
int velocidadeB = 9;
int velocidade = 0;
void setup() {
Serial.begin(38400);
 pinMode(8, OUTPUT);
 pinMode(IN1, OUTPUT);
 pinMode(IN2, OUTPUT);
 pinMode(IN3, OUTPUT);
 pinMode(IN4, OUTPUT);
 }
 
void loop()
{
  if(Serial.available()>0)
  {    
    char data= Serial.read();
    Serial.println(data);
    int dataint = data - '0';
    dataint = 25*dataint;
    digitalWrite(IN1,HIGH);
    digitalWrite(IN2,LOW);
    while (velocidade < dataint)
    {
      analogWrite(velocidadeA,velocidade);
      velocidade = velocidade + 5;
      delay(50);
    }
    while(velocidade > dataint)
    {
      analogWrite(velocidadeA,velocidade);
      velocidade = velocidade - 5;
      delay(50);
    }
  }
}

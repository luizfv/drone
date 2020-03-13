int IN1 = 4;
int IN2 = 5;
int IN3 = 10;
int IN4 =11;
int velocidadeA = 3;
int velocidadeB = 9;
int velocidade = 0;
char data;
void setup() 
{
  Serial.begin(38400);
  pinMode(8, OUTPUT);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
}
 
void loop()
{
  inicio:
  if(Serial.available()>0)
  {    
      data = Serial.read();
      Serial.println(data);
      int dataint = data - '0';
      dataint = 25*dataint;
      switch(data)
      {
        case 'a':
        digitalWrite(IN1,HIGH);
        digitalWrite(IN2,LOW);
        do
        {
          analogWrite(velocidadeA,velocidade);
          velocidade = velocidade + 255;
          delay(50);
          goto inicio;
        } while (velocidade != 255);
        case 'b':
        digitalWrite(IN3,HIGH);
        digitalWrite(IN4,LOW);
        do
        {
          analogWrite(velocidadeB,velocidade);
          velocidade = velocidade + 255;
          delay(50);
          goto inicio;
        }while (velocidade != 255);
        case 'c':
        digitalWrite(IN1,HIGH);
        digitalWrite(IN2,LOW);
        do
        {
          analogWrite(velocidadeA,velocidade);
          velocidade = velocidade - 255;
          delay(50);
          goto inicio;
        } while (velocidade != 0);
        case 'd':
        digitalWrite(IN3,HIGH);
        digitalWrite(IN4,LOW);
        do
        {
          analogWrite(velocidadeB,velocidade);
          velocidade = velocidade - 255;
          delay(50);
          goto inicio;
        }while (velocidade != 0);
      }
  }
}

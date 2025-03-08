# Sensor-de-Gas
Criamos um sensor de gas utilizando o arduino que tinha como intuito , fazer a medição do gas .

const int sensorPin = A0; // Pino do sensor de gás 
const int ledVerde = 8; // Pino do LED verde
const int ledVermelho = 9; // Pino do LED vermelho 
const int buzzer = 10; // Pino do buzzer 
int valorLido; // Variável para armazenar a leitura do sensor
void setup() {
 pinMode(ledVerde, OUTPUT);
 pinMode(ledVermelho, OUTPUT);
 pinMode(buzzer, OUTPUT);
Aqui estamos configurando os LEDs e o 
buzzer como saídas
 Serial.begin(9600);
 void loop() {
 valorLido = analogRead(sensorPin);
 Serial.print("Valor lido: ");
 Serial.println(valorLido);
 if (valorLido => 200) { // 200 é o valor que indica perigo
 digitalWrite(ledVerde, HIGH); // Acende o LED verde (sinal de segurança)
digitalWrite(ledVermelho, LOW); // Apaga o LED vermelho
digitalWrite(buzzer, LOW); // Desliga o buzzer
 Serial.println("Condição: Segurança (LED Verde)") // Imprime no monitor serial
 else if (valorLido > 200 && valorLido < 400) {
digitalWrite(ledVerde, LOW); // Apaga o LED verde
digitalWrite(ledVermelho, HIGH); // Acende o LED vermelho 
(sinal de alerta)
digitalWrite(buzzer, LOW); // Desliga o buzzer
Serial.println("Condição: Alerta (LED Vermelho)"); // Imprime no monitor serial
else if (valorLido >= 401) {
digitalWrite(ledVerde, LOW); // Apaga o LED verde
digitalWrite(ledVermelho, HIGH); // Acende o LED vermelho 
(sinal de perigo)
digitalWrite(buzzer, HIGH); // alarme sonoro
Serial.println("Condição: Perigo (LED Vermelho + Buzzer)"); // Imprime no monitor serial
 }
 delay(1000);
}

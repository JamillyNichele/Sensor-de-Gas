A detecção de gases inflamáveis é uma questão essencial em diversos ambientes, 
seja para segurança residencial, industrial ou em veículos movidos a gás. Este artigo 
apresenta o desenvolvimento de um sistema de detecção de gases inflamáveis 
utilizando uma plataforma Arduino e o sensor MQ-2. O projeto integra indicadores 
visuais (LEDs), sonoros (buzzer) e programação personalizada para monitorar 
concentrações de gás no ar. Além disso, o sistema foi projetado para ser acessível e 
replicável, com custo reduzido e montagem simplificada em protoboard. Durante os 
testes, foram avaliados o tempo de resposta, a sensibilidade do sensor e a eficiência 
dos alertas. Os resultados demonstraram que o sistema é funcional e pode ser 
melhorado com tecnologias de comunicação para alertas remotos, além de sensores 
mais avançados para aumentar a precisão. O estudo também destaca a versatilidade 
do Arduino na implementação de soluções práticas e de baixo custo. Este trabalho 
reforça a aplicabilidade do Arduino na criação de dispositivos de segurança acessíveis 
e destaca o potencial de aprimoramentos futuros, incluindo integração com sistemas 
inteligentes e automação avançada.

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

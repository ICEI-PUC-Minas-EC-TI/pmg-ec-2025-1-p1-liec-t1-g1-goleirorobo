# TÍTULO DO PROJETO

`Pontífica Universidade Católica de Minas Gerais-Coração Eucarístico`

`Engenhraria de Computação`

`1°`

`Laboratório de Introdução a Computação`


## Integrantes

* Carlos Eduardo Farias de Oliveira
* Eddu Fagundes Fernandes
* Gabriel Silva Cardoso
* Henrique Silva Guimarães
* Pedro Henrique de Jesus
* Ulisses Augusto Oliveira da Silva Vieira

## Orientador

* Felipe Augusto Lara Soares
* Naísses Zóia Lima
* Sandro Jerônimo de Almeida
## Resumo

O trabalho em pauta, define o funcionamento de um goleiro de futebol que consegue fazer defesas de níveis fáceis, médios e difíceis. O objetivo principal do jogo é conseguir fazer gols nos determinados níveis selecionados pelo aplicativo app inventor, ligado ao jogo diretamente pelo celular.

# Código (do arduino ou esp32)

#include <ESP32Servo.h>
#include <BluetoothSerial.h>

#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run `make menuconfig` to and enable it
#endif

BluetoothSerial SerialBT;
int valorRecebido = 0;  // 0 = não definido, 1 = Fácil, 2 = Médio, 3 = Difícil

// Definição dos sensores por quadrante
#define TRIG_Q1 25
#define ECHO_Q1 26
#define TRIG_Q2 5
#define ECHO_Q2 18
#define TRIG_Q3 27
#define ECHO_Q3 35
#define TRIG_Q4 22
#define ECHO_Q4 23
#define TRIG_Q5 32
#define ECHO_Q5 33
#define TRIG_Q6 15
#define ECHO_Q6 16

#define SERVO_PIN 14    // Pino PWM válido para o servo

Servo goleiro;
const int distanciaDefesa = 13; // cm

// Pré-configuração dos ângulos de defesa
const int angulosDefesa[6] = {180, 0, 160, 30, 120, 60};  // Posições pré-mapeadas

// Sistema de dificuldade
unsigned long tempoReacao = 0;  // Padrão: médio (100ms)
const unsigned long temposDificuldade[3] = {50, 20, 0}; // [Fácil, Médio, Difícil]

const int trigPins[] = {TRIG_Q1, TRIG_Q2, TRIG_Q3, TRIG_Q4, TRIG_Q5, TRIG_Q6};
const int echoPins[] = {ECHO_Q1, ECHO_Q2, ECHO_Q3, ECHO_Q4, ECHO_Q5, ECHO_Q6};


void setup() {
  // Configura os pinos dos sensores como entrada e saída
  for (int i = 0; i < 6; i++) {
    pinMode(trigPins[i], OUTPUT);
    pinMode(echoPins[i], INPUT);
  }

  // Configuração otimizada do servo
  goleiro.setPeriodHertz(50);
  goleiro.attach(SERVO_PIN, 500, 2400);
  goleiro.write(90);  // Posição inicial

  Serial.begin(115200);
  SerialBT.begin("Goleiro"); // Nome do dispositivo Bluetooth
}

long medirDistancia(int trigPin, int echoPin) {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Timeout reduzido para 15ms (50% de redução)
  long duracao = pulseIn(echoPin, HIGH, 15000); // 
  if(duracao <= 200) return -1; // Ignore pulsos curtos (ruído)
  return duracao * 0.034 / 2;
}

void defenderQuadrante(int quadrante) {
  // Usa o tempo de reação configurado pela dificuldade
  delay(tempoReacao);
  // Acesso direto ao array pré-configurado
  goleiro.write(angulosDefesa[quadrante - 1]);
  
  
  delay(1500);
  
  goleiro.write(90);
  delay(3000);
}

void atualizarDificuldade() {
  if (SerialBT.available()) {
    int cmd = SerialBT.read();
    Serial.print("Comando BT: ");
    Serial.println(cmd);
    
    // Mapeamento dos comandos:
    // '1' = Fácil
    // '2' = Médio
    // '3' = Difícil
    if (cmd >= 1 && cmd <= 3) {
      int nivel = cmd - 1;  // Converte para índice 0-based
      tempoReacao = temposDificuldade[nivel];
      
      Serial.print("Dificuldade alterada para: ");
      Serial.println(cmd == 1 ? "Fácil" : cmd == 2 ? "Médio" : "Difícil");
    }
  }
}

void loop() {
  // Verifica atualizações de dificuldade via Bluetooth
  atualizarDificuldade();

  for (int i = 0; i < 6; i++) {
    long distancia = medirDistancia(trigPins[i], echoPins[i]);
    Serial.print("Q"); Serial.print(i + 1); Serial.print(": "); Serial.println(distancia);

    if (distancia > 0 && distancia <= distanciaDefesa) {
      defenderQuadrante(i + 1);
    }
  }
  
  // Delay reduzido para 20ms
  delay(20);
}odigo/README.md"> Código Fonte (.ino)</a></li>

# Aplicativo para Smartphone

[apk.Inventor.zip](https://github.com/user-attachments/files/20890170/apk.Inventor.zip)


# Apresentação

<ol>
<li><a href="Apresentacao/README.md"> Vídeo do Funcionamento</a></li>
<li><a href="Apresentacao/README.md"> Fotos do Projeto</a></li>
</ol>

# Manual de Utilização


# Documentação

<ol>
<li><a href="Documentacao/01-Introducão.md"> Introdução</a></li>
<li><a href="Documentacao/02-Metodologias Ágeis.md"> Metodologias Ágeis</a></li>
<li><a href="Documentacao/03-Desenvolvimento.md"> Desenvolvimento </a></li>
<li><a href="Documentacao/04-Testes.md"> Testes </a></li>
<li><a href="Documentacao/05-Conclusão.md"> Conclusão </a></li>
<li><a href="Documentacao/06-Referências.md"> Referências </a></li>
</ol>


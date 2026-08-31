# Prática: Controle de Microservo com Potenciômetro

[![Simular no Tinkercad](https://img.shields.io/badge/Simular%20no-Tinkercad-orange?style=for-the-badge&logo=autodesk)](COLOQUE_AQUI_O_LINK_DO_SEU_PROJETO)

## Descrição do Projeto

Este projeto implementa um sistema de controle de um microservo utilizando um Arduino UNO e um potenciômetro.

O potenciômetro funciona como uma entrada analógica, permitindo que o Arduino leia sua posição. De acordo com o valor lido, o Arduino controla o ângulo de rotação do microservo.

Ao girar o potenciômetro, o valor da entrada analógica é alterado. Esse valor é convertido para uma faixa de ângulos entre **0° e 180°**, fazendo com que o microservo acompanhe o movimento realizado no potenciômetro.

Dessa forma, o projeto demonstra a utilização de uma entrada analógica para controlar um atuador através do Arduino.

---

## Sequência de Funcionamento

- O potenciômetro é girado pelo usuário.
- O Arduino realiza a leitura do valor analógico.
- O valor lido é convertido para um ângulo entre 0° e 180°.
- O Arduino envia o comando correspondente ao microservo.
- O microservo gira para a posição determinada.
- Conforme o potenciômetro é movimentado, o ângulo do servo é atualizado.

### Funcionamento do Sistema

| Componente | Função |
| :---: | :--- |
| Potenciômetro | Controla o valor da entrada analógica |
| Arduino UNO | Processa a leitura e controla o servo |
| Microservo | Gira de acordo com a posição do potenciômetro |

---

## Materiais Utilizados

| Qtd | Componente |
| :---: | :--- |
| 1 | Placa Arduino UNO |
| 1 | Protoboard |
| 1 | Microservo |
| 1 | Potenciômetro |
| — | Fios Jumper macho-macho |

---

## Imagem do Circuito

![Circuito Controle de Microservo com Potenciômetro](imagem-do-circuito.png)

---

## Código Utilizado

```cpp
#include <Servo.h>

// Cria o objeto do microservo
Servo meuServo;

// Pino do potenciômetro
const int potenciometro = A0;

// Pino do microservo
const int pinoServo = 7;

// Variáveis
int leitura;
int angulo;

void setup() {
  // Define o pino do servo
  meuServo.attach(pinoServo);

  // Inicia a comunicação serial
  Serial.begin(9600);
}

void loop() {
  // Faz a leitura do potenciômetro
  leitura = analogRead(potenciometro);

  // Converte o valor para um ângulo entre 0 e 180 graus
  angulo = map(leitura, 0, 1023, 0, 180);

  // Move o servo para o ângulo correspondente
  meuServo.write(angulo);

  // Mostra os valores no monitor serial
  Serial.print("Valor do potenciometro: ");
  Serial.print(leitura);

  Serial.print(" | Angulo do servo: ");
  Serial.println(angulo);

  // Pequeno intervalo
  delay(15);
}
```

---

## Funcionamento

O potenciômetro fornece ao Arduino um valor analógico entre **0 e 1023**. Esse valor é convertido pela função `map()` para uma faixa de **0° a 180°**.

Assim, ao girar o potenciômetro, o microservo acompanha a mudança e altera sua posição de acordo com o valor recebido.

## Link do Projeto no Tinkercad
https://www.tinkercad.com/things/0W9XRa6BM2r-fantabulous-wluff-jofo/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard&sharecode=SdengD5ufTZ1x02Ltmkj9FIkDWS4lzuVEmFALb53ld4

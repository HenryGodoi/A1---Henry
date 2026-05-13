
Identifique as entradas e saídas do sistema:
Botão iniciar - Acende o LED Amarelo e o LED Verde
Botão parar - Acende o LED Vermelho e Desliga os LEDs Verde e o Amarelo
Botão reset - Desliga todos os LEDs
2° Potenciômetro - Conforme o valor do potenciômetro, irá acender um, dois ou três LEDs, significando 1° LED aceso = Nível Baixo, 1° LED e o 2° LED acessos = Nível Médio, Todos os LEDs acessos = Nível Alto.



Apresente todos os componentes do sistema e para que eles servem:

Botão Iniciar - O sistema irá ler o valor que o botão foi pressionado e iniciará a execução do processo durante o tempo determinado pelo 1° Potenciômetro, ao receber o valor do botão pressionado, irá acender o LED Amarelo e o LED Verde, após o tempo determinado chegar ao seu fim, o sistema irá encerrar a execução do processo e retornar ao estado inicial;
Botão Parar - Irá interromper imediatamente o processo do sistema, independente da situação, acende o LED Vermelho e Desliga os LEDs Verde e o Amarelo;
Botão Reset - Irá reiniciar o comportamento do sistema e retornar ao estado inicial e desligará todos os LEDs;
1° Potenciômetro - Irá ajustar o tempo da execução do processo. o valor varia de 0 a 1023 e irá ser interpretado pelo sistema como um tempo entre 1 e 10 segundos;
2° Potenciômetro - Será utilizado para ajustar a intensidade do processo, conforme o valor do potenciômetro, irá acender um, dois ou três LEDs, significando 1° LED aceso = Nível Baixo, 1° LED e o 2° LED acessos = Nível Médio, Todos os LEDs acessos = Nível Alto.;
LED Verde - Significa que o sistema está ativo;
LED Amarelo - Significa que o processo está em execução;
LED Vermelho - Significa que o sistema está parado.
Arduino Uno R3 - Placa de desenvolvimento utilizada


Apresente as regras de funcionamento a serem implementadas:
1° Passo:
Determinar o tempo do processo com o 1° Potenciômetro;
Ajustar a intensidade do processo com o 2° Potenciômetro;
LEDs que demonstram a intensidade do processo acende;
Pressionar Botão Iniciar;
LED Amarelo e LED Verde acende;

2° Passo (Caso for necessário):
Após concluir o 1° Passo, você percebe que alguma coisa entrou na máquina e decide interromper ela:
Pressionar Botão Parar;
LED Amarelo e LED Verde se apagam;
LED Vermelho acende;
1° Opção - Tirar a coisa que entrou na máquina e apertar o Botão Iniciar novamente ou 2° Opção - Apertar o Botão Reset e depois apertar o Botão Iniciar. (Você optou pela 2° Opção);

3° Passo (Caso você tenha escolhido a 2° Opção)
Pressionar Botão Reset;
Desliga todos os LEDs;
Pressionar Botão Iniciar;
LED Amarelo e LED Verde se acendem;



Explique como você utilizaria estruturas if para controlar o sistema:


IF botao1 == 1:
    Iniciar execução do processo
    LED Amarelo = ALTO
    LED Verde = ALTO
IF potenciometro2 = 1:
   1° LED Azul = ALTO
	   2° LED Azul = BAIXO
   3° LED Azul = BAIXO
IF potenciometro2 = 2:
    1° LED Azul = ALTO
	    2° LED Azul = ALTO
    3° LED Azul = BAIXO
IF potenciometro2 = 3:
    1° LED Azul = ALTO
	    2° LED Azul = ALTO
    3° LED Azul = ALTO
   aguardar (potenciometro1)
		  LED Amarelo = BAIXO
		  LED Verde = BAIXO
		  1° LED Azul = BAIXO
	              2° LED Azul = BAIXO
  3° LED Azul = BAIXO

# LINK DO PROJETO:
https://www.tinkercad.com/things/hwS6EXxf2CJ-a1-henry?sharecode=Pvw3yUrSQtdP-fMV2aWqqEri-WKsUzN62If9jin-qqs

# Código:
```bash
int botao = 0;

int pot1 = 0;

int pot2 = 0;

void setup()
{
  pinMode(A1, INPUT);
  pinMode(A2, INPUT);
  pinMode(2, INPUT);
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(9, OUTPUT);
}

void loop()
{
  pot1 = map(analogRead(A1), 0, 1023, 1, 10);
  pot2 = map(analogRead(A2), 0, 1023, 1, 3);
  botao = digitalRead(2);
  if (botao == 1) {
    digitalWrite(13, HIGH);
    digitalWrite(12, HIGH);
    if (pot2 == 1) {
      digitalWrite(11, HIGH);
      digitalWrite(10, LOW);
      digitalWrite(9, LOW);
    }
    if (pot2 == 2) {
      digitalWrite(11, HIGH);
      digitalWrite(10, HIGH);
      digitalWrite(9, LOW);
    }
    if (pot2 == 3) {
      digitalWrite(11, HIGH);
      digitalWrite(10, HIGH);
      digitalWrite(9, HIGH);
    }
    delay(1000 * pot1); // Wait for 1000 * pot1 millisecond(s)
    digitalWrite(13, LOW);
    digitalWrite(12, LOW);
    digitalWrite(11, LOW);
    digitalWrite(10, LOW);
    digitalWrite(9, LOW);
  }
}
```

<img width="442" height="365" alt="image" src="https://github.com/user-attachments/assets/bdfefb26-3f39-4e4d-ab41-6ee2a1ec8dd4" />

<img width="401" height="763" alt="image" src="https://github.com/user-attachments/assets/c2d9b1a9-c6b8-4f6e-80a8-b62ea955c779" />

<img width="364" height="441" alt="image" src="https://github.com/user-attachments/assets/956664a7-0237-4911-ba09-e9b23fada9a9" />

<img width="358" height="398" alt="image" src="https://github.com/user-attachments/assets/29c85bcf-041b-4471-ae84-dd40c8bfa652" />

<img width="357" height="457" alt="image" src="https://github.com/user-attachments/assets/4c87c04f-e38c-4237-8cac-edb1e835585e" />




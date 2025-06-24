
# Materiais

Os materiais utilizados no projeto foram:                  
1 - Servo Motor SG-5010 Tower Pro,1 - Módulo WiFi Bluetooth ESP32-WROOM-32U Ipex,1 - Pacote Jumpers- Macho/Fema - 40 unidades de 20cm,6 - Módulo Sensor de Distância Ultrassônico US-015,1 - Protoboard 830 Pontos,1 - Tábua de madeira 30cm por 30cm,1 - Adesivo do campo 30cm por 30cm,1 - Jogador Club Gulliver,1 - Bola,1 - Tirante (Gol).
1 - Goleiro,1 - Tela (rede do gol).



# Desenvolvimento

O projeto Goleiro Robô foi desenvolvido em grupo ao longo de quatro sprints. No início, planejamos os componentes, dividimos as tarefas, elaboramos o orçamento e organizamos o fluxo de trabalho utilizando GitHub e Trello.

Cada integrante ficou responsável por uma parte do projeto, como programação no Arduino, montagem da estrutura física, desenvolvimento do app no App Inventor e produção da documentação.

Entre as principais atividades estiveram a montagem do goleiro, a programação dos sensores e a criação do aplicativo. A bola foi detectada com sensor ultrassônico, a estrutura foi montada e o motor lateral foi testado com sucesso, garantindo movimentos precisos, rápidos e com bom alcance. 

## Desenvolvimento do Aplicativo

![3b520755-be01-4fef-ab9c-5acdca9a8135](https://github.com/user-attachments/assets/b0b0c85b-2e15-4102-b084-a090c74faaf1)
🏗️ Estrutura da Tela Inicial
🎨 Visual
Imagem de fundo: Estádio iluminado (definida como plano de fundo da tela).

Título: "GOLEIRO AUTOMÁTICO" com fonte grande e verde.

Ícones: Mãos douradas (imagens) ao lado do título.

Botão "JOGAR": Grande, verde, centralizado – leva para a próxima tela.

Botão "PAREAR GOLEIRO": Pequeno, no canto inferior esquerdo – ativa o Bluetooth.

Texto extra: “Texto para Legenda1” (parece ser um rótulo não finalizado).

⚙️ Lógica (Blocos)
Ao clicar em "JOGAR" → Abre a próxima tela do jogo.

Ao clicar em "PAREAR GOLEIRO" → Inicia conexão Bluetooth com um dispositivo externo (robô goleiro, por exemplo).


![c19fadba-eab3-4a6c-9cff-e6af8c01e919](https://github.com/user-attachments/assets/b2fe4d70-3838-41c3-aa13-86a4d6278e86)
Tela: Escolha de dificuldade (Fácil, Médio, Difícil).

Fundo: Estádio iluminado, clima esportivo.

Botões:

Verde (Fácil)

Amarelo (Médio)

Vermelho (Difícil)
Com efeitos de brilho (neon) e bordas arredondadas.

Texto: “ESCOLHA DIFICULDADE” com fonte futurista e azul brilhante.

Funcionalidade: Cada botão leva para um modo de jogo correspondente.

Feito com: Pode ser desenvolvido em Flutter, Unity, Android ou outro motor de apps.


### Código

🔧 Lógica:
Ao clicar em "JOGAR":

open another screen → Tela de dificuldade.

Ao clicar em "FÁCIL", "MÉDIO" ou "DIFÍCIL":

Define o nível de dificuldade com uma variável global (ex: set global dificuldade to "Fácil").

Abre a próxima tela de jogo (open another screen with start value).

Ao clicar em "PAREAR GOLEIRO":

Abre uma tela para pareamento Bluetooth com um módulo (ex: HC-05).

Usa componentes BluetoothClient para conectar ao dispositivo.

🔌funcionalidade adicional (Bluetooth):
O app esta conectado a um goleiro automatizado com motores/servos.

Envia comandos via Bluetooth conforme o nível de dificuldade.

Recebe dados de sensores ou controle remoto.

## Desenvolvimento do Hardware

### Montagem

 Montagem do Projeto
 
O projeto consistiu em montar um goleiro automático que se move com base na detecção de uma bola, utilizando um ESP32, sensor ultrassônico e um servo motor.

Planejamento: Foram escolhidos os componentes (ESP32, sensor, servo e estrutura do goleiro).


Montagem eletrônica:

O sensor ultrassônico foi ligado ao ESP32 para detectar a distância da bola.

O servo motor foi conectado para mover o goleiro lateralmente.


Programação:

O código em C++ (via Arduino IDE) media a distância da bola.

Dependendo da posição detectada, o ESP32 movia o servo para esquerda, centro ou direita.


Montagem física:

A estrutura foi feita com uma base de madeira e as traves de ferro, colocado um adesivo do campo na superficie da madeira .

O goleiro foi preso ao braço do servo motor.


Testes:

Foram feitos ajustes na detecção e no movimento do servo.

O goleiro respondia automaticamente à aproximação da bola.

### Desenvolvimento do Código

O código foi desenvolvido para controlar um servo motor com base nas leituras de um sensor ultrassônico (HC-SR04) usando o ESP32. O funcionamento básico envolve:

Configuração inicial:

Definição dos pinos do TRIG e ECHO do sensor.

Inicialização do servo motor (em um pino PWM).

Configuração da serial para depuração.

Leitura da distância:

O código emite um pulso no TRIG.

Mede o tempo de resposta no ECHO.

Converte o tempo em distância em centímetros.

Movimento do goleiro:

Se a bola está próxima (abaixo de certo valor), o código decide a direção (esquerda, centro ou direita).

O servo motor se move para a posição correspondente (com servo.write(ângulo)).

Loop contínuo:

A função loop() executa continuamente a leitura do sensor e atualiza a posição do servo conforme necessário.


## Comunicação entre App e Hardware

O aplicativo foi configurado para realizar o pareamento via Bluetooth com o hardware, que utiliza uma placa com suporte a Wi-Fi e Bluetooth padrão. Para isso, foram utilizados plugins do App Inventor que permitem a conexão entre o dispositivo móvel e o hardware, possibilitando a troca de informações.

Durante o pareamento, o usuário pode selecionar o nível de dificuldade do goleiro. Essa seleção é enviada ao hardware na forma de um valor decimal inteiro, que representa um preset de dificuldade. Cada nível influencia no tempo de reação do goleiro, ajustando o delay de resposta do sistema.

Para garantir maior robustez, foi implementado um sistema de tratamento de falhas no código fonte, incluindo um aviso (warn) em caso de erros. Além disso, foi adicionado um monitoramento via terminal, que informa o status da conexão Bluetooth e qualquer alteração realizada na dificuldade selecionada.

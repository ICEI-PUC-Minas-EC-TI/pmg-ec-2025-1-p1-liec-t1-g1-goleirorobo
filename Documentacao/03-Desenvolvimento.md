
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

Descreva o desenvolvimento do código do aplicativo.

## Desenvolvimento do Hardware

### Montagem

Descreva como foi o processo da montagem do projeto.

### Desenvolvimento do Código

Descreva como foi o desenvolvimento do código do arduino/ESP.

## Comunicação entre App e Hardware

Descreva como foi o processo de comunicação entre App e arduino/ESP.

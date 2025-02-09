Resumo do Funcionamento do Código
Este código é projetado para controlar uma matriz de LEDs NeoPixel (WS2812B) e um display OLED SSD1306 usando um microcontrolador Raspberry Pi Pico. 
O código também inclui a leitura de botões e a exibição de informações no display OLED com base nas interações do usuário.

Vídeo Demonstrando o Funcionamento do Projeto:https://youtu.be/PgtJErYjKpo

Funcionalidades Principais
1)Controle de LEDs NeoPixel:

O código controla uma matriz de 25 LEDs NeoPixel, organizados em uma grade 5x5.

Os LEDs podem ser configurados para exibir diferentes padrões de números (0 a 9) com base na entrada do usuário.

A função npSetPattern mapeia os padrões de números para os LEDs, acendendo-os de acordo com a matriz de cores definida.

2)Display OLED SSD1306:

O código utiliza um display OLED SSD1306 para exibir informações visuais.

O display mostra o estado dos LEDs Verde e Azul, que são controlados pelos botões A e B, respectivamente.

O display também exibe o caractere digitado pelo usuário via comunicação serial.

3)Leitura de Botões:

Dois botões (A e B) são usados para alternar o estado dos LEDs Verde e Azul.

A função gpio_irq_handler gerencia as interrupções dos botões, alternando o estado dos LEDs e atualizando o display OLED.

4)Comunicação Serial:

O código permite a entrada de caracteres via comunicação serial (USB).

O caractere digitado pelo usuário é exibido no display OLED e também determina qual padrão de número será exibido na matriz de LEDs.

5)Inicialização e Configuração:

O código inicializa os pinos GPIO para os botões e LEDs.

Configura a comunicação I2C para o display OLED.

Inicializa a máquina de estado PIO para controlar os LEDs NeoPixel.

//

Estrutura do Código:

1)Inicialização:

inoutput_init(): Configura os pinos GPIO para os botões e LEDs.

npInit(): Inicializa a máquina de estado PIO para controlar os LEDs NeoPixel.

i2c_init(): Configura a comunicação I2C para o display OLED.

2)Interrupções:

gpio_irq_handler(): Gerencia as interrupções dos botões, alternando o estado dos LEDs e atualizando o display.

3)Controle de LEDs:

npSetLED(): Define a cor de um LED específico.

npClear(): Limpa todos os LEDs.

npWrite(): Envia os dados de cor para os LEDs.

npSetPattern(): Mapeia um padrão de número para a matriz de LEDs.

4)Display OLED:

ssd1306_init(): Inicializa o display OLED.

ssd1306_draw_string() e ssd1306_draw_char(): Desenha strings e caracteres no display.

5)Loop Principal:

O loop principal gerencia a atualização do display OLED, a leitura de caracteres via serial e a exibição dos padrões de números na matriz de LEDs.


//


Como Usar
1)Entrada Serial:

Conecte o Raspberry Pi Pico ao computador via USB.

Use um terminal serial para enviar caracteres (0-9) para o Pico.

O caractere enviado será exibido no display OLED e o padrão correspondente será exibido na matriz de LEDs.

2)Botões:

Pressione o botão A para alternar o estado do LED Verde.

Pressione o botão B para alternar o estado do LED Azul.

O estado dos LEDs será refletido no display OLED.

//

Dependências
Bibliotecas:

pico/stdlib.h: Para funções básicas do Pico.

hardware/i2c.h: Para comunicação I2C.

hardware/pio.h: Para controle da máquina de estado PIO.

ws2818b.pio.h: Para controle dos LEDs NeoPixel.

inc/ssd1306.h: Para controle do display OLED.

//

Exemplo de Uso:
Envie o caractere '5' via serial para exibir o número 5 na matriz de LEDs.

Pressione o botão A para ligar/desligar o LED Verde.

Pressione o botão B para ligar/desligar o LED Azul.

Este código é uma demonstração de como controlar LEDs NeoPixel, um display OLED e interagir com botões usando o Raspberry Pi Pico. 
Ele pode ser expandido para incluir mais funcionalidades, como exibir diferentes padrões ou interagir com mais dispositivos.

### **Glossário de Termos e Comandos para Torno CNC (Comando Fanuc)**

Este glossário explica os principais códigos e termos utilizados na programação CNC para torneamento, especialmente os que aparecem no programa da peça `FLANGE-EIXO`.

---

### **1. Códigos G (Funções Preparatórias)**

Os Códigos G definem o tipo de movimento ou a modalidade de operação que a máquina deve executar.

*   **G00 (ou G0) - Posicionamento Rápido:**
    *   Move a ferramenta na maior velocidade possível para uma coordenada específica. **NÃO se usa para cortar material**, apenas para movimentação no ar.

*   **G01 (ou G1) - Interpolação Linear:**
    *   Move a ferramenta em uma linha reta (seja em um eixo ou em ambos simultaneamente, criando um cone) a uma velocidade de avanço controlada (`F`). É o principal comando para usinar retas e cones.

*   **G02 (ou G2) - Interpolação Circular Horária:**
    *   Move a ferramenta em um arco no sentido horário. É usado para usinar raios convexos (externos) ou côncavos (internos). Requer um ponto final (`X`, `Z`) e o valor do raio (`R`) ou as coordenadas do centro do arco (`I`, `K`).

*   **G03 (ou G3) - Interpolação Circular Anti-horária:**
    *   Move a ferramenta em um arco no sentido anti-horário. Usado para usinar raios côncavos (externos) ou convexos (internos). Também requer um ponto final e `R` ou `I`, `K`.

*   **G21 - Programação em Milímetros:**
    *   Define que todas as unidades de medida do programa são em milímetros. (O oposto é G20, para polegadas).

*   **G28 - Retorno ao Ponto de Referência (Zero Máquina):**
    *   Envia os eixos para uma posição fixa de referência da máquina (Home). `G28 U0 W0` faz isso de forma segura, passando primeiro por uma posição intermediária.

*   **G40 - Cancela Compensação de Raio da Ferramenta:**
    *   Desativa a compensação do raio da ponta da ferramenta (G41/G42). É um comando de segurança usado no início e no fim do programa.

*   **G50 - Limite de Rotação do Fuso:**
    *   Define a rotação máxima (RPM) que o fuso pode atingir. É um comando de segurança, especialmente quando se usa G96.

*   **G96 - Velocidade de Corte Constante (VCC):**
    *   A máquina ajusta automaticamente a rotação (RPM) do fuso com base no diâmetro que está sendo usinado para manter a velocidade de corte (em metros/minuto) constante. Isso resulta em um melhor acabamento superficial.

*   **G99 - Avanço por Rotação:**
    *   Define que o valor do avanço (`F`) será medido em milímetros por rotação do fuso (mm/rot). É o padrão para torneamento.

---

### **2. Códigos M (Funções Miscelâneas)**

Os Códigos M controlam funções auxiliares da máquina, como ligar/desligar o fuso, refrigeração, etc.

*   **M03 - Ligar Fuso no Sentido Horário:**
    *   Aciona a rotação da placa no sentido horário (o mais comum para ferramentas de corte à direita).

*   **M05 - Desligar Fuso:**
    *   Para a rotação da placa.

*   **M08 - Ligar Fluido de Refrigeração:**
    *   Aciona a bomba do óleo solúvel.

*   **M09 - Desligar Fluido de Refrigeração:**
    *   Desliga a bomba do óleo.

*   **M30 - Fim de Programa e Reset:**
    *   Indica o final do programa, para a execução, desliga o fuso e a refrigeração e "rebobina" o programa para o início.

---

### **3. Parâmetros e Endereços (Letras)**

*   **O** - Número do Programa (Ex: `O1025`).
*   **N** - Número da Linha ou Bloco (Ex: `N40`). Ajuda na organização e na busca de linhas.
*   **X** - Coordenada no Eixo X (movimento diametral).
*   **Z** - Coordenada no Eixo Z (movimento longitudinal/comprimento).
*   **U** - Coordenada incremental no Eixo X.
*   **W** - Coordenada incremental no Eixo Z.
*   **F** - Avanço (Feed Rate). Velocidade de corte da ferramenta (em mm/rot com G99).
*   **S** - Velocidade (Speed). Com `G96`, é a velocidade de corte em m/min. Com `G97`, seria a rotação em RPM.
*   **T** - Ferramenta (Tool). `T0101`: os dois primeiros dígitos (`01`) chamam a ferramenta na posição 1 da torre; os dois últimos (`01`) chamam o corretor de geometria/desgaste nº 1.
*   **R** - Raio do Arco. Usado com `G02` e `G03` para definir o raio da interpolação circular.

---

### **4. Termos Gerais de Usinagem e CNC**

*   **Acabamento:** O último passe de usinagem, com pouco material a ser removido, focado em atingir as dimensões finais e a qualidade de superfície desejada.
*   **Avanço (Feed Rate):** A velocidade com que a ferramenta de corte se move ao longo da peça.
*   **Chanfro:** Uma pequena borda angular usinada para quebrar um canto vivo.
*   **Comando Fanuc:** Um dos sistemas operacionais (CNC - Controle Numérico Computadorizado) mais populares do mundo para máquinas-ferramenta. É o "cérebro" da máquina.
*   **Compensação de Raio:** Um recurso do CNC que ajusta automaticamente a trajetória da ferramenta para compensar o raio da sua ponta, garantindo que o perfil final da peça seja exato.
*   **Corretor de Ferramenta (Offset):** Uma tabela na memória do CNC onde se armazenam as medidas geométricas e o desgaste de cada ferramenta. O comando `T0101` ativa o corretor 1.
*   **Desbaste:** O processo de remover a maior parte do material bruto (sobremetal) da peça, de forma rápida, preparando-a para a operação de acabamento.
*   **Fuso (Spindle):** O eixo principal do torno que gira e segura a peça através da placa.
*   **Romi GL 240M:** O modelo específico do seu torno CNC.
*   **Velocidade de Corte (VC):** A velocidade relativa entre a aresta de corte da ferramenta e a superfície da peça. É um parâmetro crucial para a vida útil da ferramenta e o acabamento. Medida em metros por minuto (m/min).

![image](https://github.com/user-attachments/assets/3f70669c-53cd-4f2f-872f-b7db86df3cc6)

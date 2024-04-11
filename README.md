# processador-MIPS-simples
Processador feito no logisim para a disciplina de Arquitetura e Organização de Computadores.
<br>
Esse processador é inspirado no processador MIPS, sendo mais simples, executando menos instruções e de forma de diferente.

## Hardwares
- PC: Registrador de 32 bits que armazena o endereço para a próxima instrução, para tal soma 4 ao valor atual.
- Memória de instruções: Armazena as instruções a serem executadas. Dela saem 32 bits.
- Banco de Registradores: Guarda 4 registradores de 32 bits. Recebe os bits de instrução da memória e identifica quais registradores seram utilizados, também recebe os dados a serem escritos e um bit de sinal para indicar se será escrito algo. A sua saída são os dados armazenados no registradores indicados.
- ULA: Unidade Lógica Aritmética recebe os dados do banco de registradores e executa operações de soma, subtraçã, multiplicação ou comparação. Recebe da Unidade de Controle um código de 4 bits que indica qual operação realizar. Envia os dados calculados de volta ao Banco de Registradores.
- Unidade de Controle: Recebe os 4 primeiros bits (31 - 28) da instrução vind da Memória de Instruções, então baseado nos bits envia sinais que indicam que operações seram realizadas pelo processador.
- Memória de Dados: Recebe 8 bits que indicam qual endereço será acessado, 32 bits com os dados a serem escritos na memória vindo dos registradores. Recebe um sinal de leitura e outro de escrita da Unidade de Controle para decidir se uma dessas operações será realizada. Envia os dados para o banco de registradores.

## Instruções
As instruções são indicadas pelos bits [31-28] dos 32 que vem da memória de instruções.
<br>
Formato de instruções do tipo R: | Opcode [31-28] | rd [27-24] | rs [23-20] | rt [19-16] | não usado [15-0 |
<br>
Formato de instruções load/store: | opcode [31-28] | rs [27-24] | imediato [23-16]
<br>
Formato da instrução branch: | opcode 31-28 | nao usado [27-24] | rs [23-20] | rt [19-16] | imediato [15-0] |
<br>
Formato da instrução jump: | opcode [31-28] | imediato [27-0] |
<br>
Opcode de cada instrução:
- Add (Soma): 0000
- Sub (Subtração): 0001
- Multiplicação: 0010
- Load: 0011
- Store: 0100
- Branch: 1001
- Jump: 1000

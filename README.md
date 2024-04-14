# Como utilizar a placa DE10-Lite no Logisim

O Logisim permite implemetarmos nossos circuitos em placas FPGA sem a necessidade de descrever o hardware utilizando uma linguagem de descrição, como o SystemVerilog ou VHDL. Neste tutorial, irei ensinar como fazer o passo-a-passo para exportar um projeto no Logisim para placa FPGA DE10-Lite.

## Requisitos

1. Quartus Prime devidamente instalado;
2. USB Blaster instalado;
3. Arquivo de configuração da FPGA para o Logisim. O arquivo encontra-se nesse repositório (créditos: Gonçalo Martins, em http://engredu.com/)

## Tutorial

Primeiramente projete o seu circuito no Logisim. Obrigatoriamente todas as entradas e saídas devem ser nomeadas.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/4ad34e56-9f9d-4190-a109-368f01942337)

Após isso, clique em FPGA --> Sintetizar.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/c7addb7e-90af-4207-94ef-50094ba9cea5)

Na tela que abrir, clique em Settings.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/d0c48aff-79a1-4e60-ac99-46318800ee7a)

Na nova tela, clique em Adicionar um quadro.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/7dd50ccc-f4c1-4689-b851-5f3660bd4629)

Selecione o arquivo XML da placa FPGA, no caso, `DE10LITE.xml`.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/1b3cdeae-c3a2-4673-9450-cc4471b4e696)

Verifique se na lista de placas externas, consta a DE10LITE e feche a janela.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/6cd1822e-c6b3-4d2d-aaf0-ca3f9a5addfd)

Vá novamente em FPGA --> Sintetizar. Em Target Board, selecione a opção DE10Lite e verifique se a imagem da FPGA aparece na tela.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/75b3bd28-8e15-4ce1-b51b-f284392e4b3f)

Antes de efetuar a programação da FPGA, é necessário informar ao Logisim o caminho aonde o Quartus está instalado. Para isso, feche a janela anterior e clique em Arquivos --> Preferências.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/6f209e05-7c93-4eac-bd17-f0406f4ee6e3)

Na aba programa de terceiros, vá na opção Percusso da ferramenta Altera/Intel Quartus e clique no botão navegar.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/e0d5443f-7440-4f49-9685-413645c2583f)

Selecione o diretório aonde o Quartus está instalado. No meu caso, está instalado em `C:\intelFPGA_lite\23.1std\quartus\bin64\`.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/5e697a3d-f609-4976-85d7-8ad09b8aea31)

Após selecionar o diretório e fechar a janela de preferências, vá novamente em FPGA --> Sintetizar. Em Action method, selecione a opção Synthesize & Download e clique em Execute.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/916069f3-e4c3-420b-80f7-aaf3da3b89f4)

Você deverá agora mapear as entradas/saídas na placa FPGA. Para isso, na janela Component to FPGA board mapping, selecione a entrada/saída na caixa Unmapped Components e clique no recurso da FPGA desejado. No caso, mapeie as entradas em chaves e as saídas em Leds.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/4bf83d1a-5239-4198-9f34-cc7fa6585bd7)

Após finalizado, clique em Done.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/8eebcfe8-f776-47a7-b3e6-a83c516c2b6e)

Espere o processo de compilação e sintese do Quartus. 
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/9e6451eb-4c71-4a06-823e-ce0393415c9c)

Após finalizado o processo de compilação e sintese, o Logisim pergunta se a placa FPGA está conectada no computador. Se sim, clique em Sim, Download.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/29817ac6-dd39-4ca0-9aea-bfc64484dcde)

O Logisim irá começar a realizar a programação da FPGA.
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/02f5962c-b6b9-470f-af64-d8aa289e570f)

Após finalizado a programação, o seu circuito já estará na FPGA!
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/576b83c0-58c8-4ebb-8d57-785f206faab1)

## E se quiser apenas gerar os arquivos HDL?

É possível. Na tela FPGA --> Sintetizar selecione a opção Generate HDL only. 
![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/9cdd8a9c-5471-4a05-8b5b-bdbc60ae8cc2)

No console é indicado o local aonde está o projeto. No meu caso, `C:\Users\souza\logisim_evolution_workspace\somadorcompleto`

![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/df93ff98-a793-4b15-be56-3aea860bcef1)

Navege até a pasta `main\vhdl` (se você escolheu VHDL como linguagem padrão) ou `main\verilog` (se você escolheu Verilog como linguagem padrão) para ver os arquivos do projeto. Lembre que os arquivos gerados não são feitos da forma mais otimizada possível!

![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/05525ada-d7b6-419a-958d-a53e9b7bfde8)

Para trocar a linguagem de descrição utilizado, na janela de síntese de FPGA, clique em Settings.

![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/66afa84b-4742-486b-8ffb-f8c912482d5f)

Na seleção de ligaugem, escolha Verilog.

![image](https://github.com/pedrothiag/de10-lite-logisim/assets/5923790/35bf98bc-c0e1-4242-afa5-54e5890d0b95)

Repita o processo de geração de HDL. Agora o circuito em Verilog será criado!


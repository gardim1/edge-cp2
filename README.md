
# Sistema de monitoramento de luminosidade, temperatura e umidade do ar. 

Sistema de monitoramento de luminosidade, temperatura e umidade do ar no ambiente para a Vinheria Agnello, que opera como loja física e que está demandando o desenvolvimento de um portal de e-commerce, para começar a vender também na internet, mas com uma exigência básica: que a loja virtual consiga criar uma experiência do usuário similar à do atendimento presencial em sua loja física. 

Projeto realizado para monitorar o ambiente em que os vinhos ficam armazenados, realizado como Checkpoint 2 para a matéria de Edge Computing, lecionada pelo professor Lucas Demetrius.

## Link do projeto no tinkercad

https://www.tinkercad.com/things/aHSc9V4SIoV-checkpoint-2-edge-computing?sharecode=Dd0wbBlAain5Hzw9OWoQadXgDpcqAgaWR-BjH4hNikA

## Como reproduzir

Após clicar em "Iniciar simulação", sinta-se livre para clicar no fotorresistor, sensor de temperatura ou poteciômetro, para alterar seus valores. Conforme a variação feita nos sensores, o display irá exibir o status da luminosidade, temperatura e umidade.

**AVISO:** O buzzer irá soar em casos de iregularidade, então é indicável abaixar o volume do seu dispositvo.

## Autores
- [Camila Feitosa](https://github.com/camfeitosa)
- [Gabriel Matiolli](https://www.github.com/m4tiolli)
- [Gustavo Berlanga](https://www.github.com/berla1)
- [Leonardo Taschin](https://www.github.com/LeoTaschin)
- [Vinicius Gardim](https://www.github.com/gardim1)

## Dependências

Componentes utilizados no circuito:

- Arduino Uno R3
- Placa de Ensaio
- Display LCD 16x2
- Leds vermelho, amarelo e verde
- Sensor de temperatura 
- Potenciômetro
- Fotorresistor
- Buzzer Piezo
- 5 Resistores de 1000 ohm
- Jumper Cables
    
![Logo](https://gcdnb.pbrd.co/images/zIZlq7SC5Rjw.png?o=1)


## Lógica


### Luminosidade
Os vinhos agradecem lugares com penumbra, especialmente os brancos e espumantes, que sofrem mais com o contato com a luz. Em função disso, o sistema monitora a luminosidade do ambiente com LED’s da seguinte maneira:

Led verde: caso a luminosidade esteja baixa, em condição ideial, acende.

Led amarelo:  Em caso de alerta, onde a luminosidade não está ideal, acende e um buzzer soa durante 3 segundos, se a luminosidade permanecer em níveis de alerta o buzzer continuará soando.

O led vermelho: se acende quando a luminosidade está excessivamente alta e o buzzer é ativo, que toca até que as condições ideias sejam reestabelecidas.

Todos os status são exibidos no display LCD.

| LED | Valor lido pelo LDR |   Status exibido  | Buzzer ligado? |
|:----| :-----------------: | :--:|:------------: |
|Led verde| Maior que 700 | Luminosidade ideal| Não |
|Led amarelo|Menor que 700 e maior que 400|Ambiente meia a luz|Sim |
|Led vermelho| Menor que 400 |Ambiente muito claro | Sim |

### Temperatura
O calor excessivo rapidamente termina com a vida do vinho e as flutuações térmicas de mais de 3°C podem causar o aparecimento de aromas indesejados. A situação perfeita seria que ficassem constantemente sob uma temperatura de cerca de 13°C.

A tabela abaixo mostra o esquema de como funciona a exibição dos valores para o usuário. O buzzer não é acinado no caso da temperatura.

**Observação importante:** A execução do sistema real utiliza um sensor DHT11 para monitorar a temperatura. Por conta do mesmo não existir no tinkercad, a escolha foi de utilizar aquele que está disponível na plataforma.

| Valor | Status exibido | 
|:----| :-----------------: | 
|Entre 10°C e 15°C| Temp. OK | 
|Acima de 15°C|Temp. Alta | 
|Abaixo de 10°C|Temp. Baixa | 

### Humidade

A falta de umidade pode levar, por exemplo, ao ressecamento do vedante, provocando uma má vedação da garrafa, com risco de oxidação do líquido.Já o excesso de umidade pode danificar os rótulos, bem como promover a proliferação de fungos.O ideal é que seja próxima a 70% (com variação em torno de 60% a 80%).

A tabela abaixo apresenta o esquema de funcionamento do sistema de umidade.


**Observação importante:** A execução do sistema real utiliza um sensor DHT11 para monitorar a umidade do ambiente. Por conta do mesmo não existir no tinkercad, a escolha foi de utilizar aquele que está disponível na plataforma.

| Valor | Status exibido | Buzzer ligado?|
|:----| :-----------------: | :------: |
|Entre 50% e 70%| Umidade OK | Não|
|Acima de 70%|Umidade Alta | Sim |
|Abaixo de 50%|Umidade Baixa | Sim |

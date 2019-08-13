# EMG and TENS

Circuitos simples de [EMG](https://en.wikipedia.org/wiki/Electromyography) e [TENS](https://en.wikipedia.org/wiki/Transcutaneous_electrical_nerve_stimulation) para o seu braço "controlar" o braço de outra pessoa.

[Read in english](https://github.com/leandcesar/emg-and-tens/blob/master/README.md).

## Sobre

Inspirado pela [Backyard Brains](https://backyardbrains.com), projetei circuitos para usar seu sinal muscular (com EMG) para excitar e contrair o músculo de outra pessoa (com TENS). Para mais informações, leia o post "[Experiment: Advanced NeuroProsthetics: Take Someone's Free Will](https://backyardbrains.com/experiments/humanhumaninterface)" e/ou assista o vídeo do Greg Gage "[How to control someone else's arm with your brain](https://www.ted.com/talks/greg_gage_how_to_control_someone_else_s_arm_with_your_brain?)" no TED.

[![Assista ao vídeo](http://i3.ytimg.com/vi/rSQNi5sAwuc/maxresdefault.jpg)](https://www.ted.com/talks/greg_gage_how_to_control_someone_else_s_arm_with_your_brain?)

## EMG

A eletromiografia (EMG) é uma técnica eletrodiagnóstica para avaliar e registrar a atividade elétrica produzida pelos músculos esqueléticos. A EMG é realizada usando um instrumento chamado eletromiógrafo para produzir um registro chamado eletromiograma. Um eletromiógrafo detecta o potencial elétrico gerado pelas células musculares quando essas células são ativadas eletricamente ou neurologicamente.

#### Componentes 

- 1x INA106;
- 1x TL074;
- 2x 1N4148;
- 1x Potenciometro 200K ohm;
- Capacitores: 1uF (3x) e 0.01uF (1x);
- Resistores: 1M ohm (2x), 10K ohm (2x), 1K ohm (1x), 150K ohm (4x) e 82K ohm (1x).

#### Esquemático

O arquivo do esquemático em [Proteus](https://www.labcenter.com/) pode ser visto [aqui](https://github.com/leandcesar/emg-and-tens/blob/master/EMG).

![Esquemático do EMG](https://github.com/leandcesar/emg-and-tens/blob/master/EMG/EMG-sch.png)

#### Protoboard

![EMG protoboard](https://github.com/leandcesar/emg-and-tens/blob/master/EMG/EMG-proto.png)

## TENS

Neuroestimulação elétrica transcutânea (TENS) é o uso de corrente elétrica produzida por um dispositivo para estimular os nervos para fins terapêuticos. A unidade é geralmente ligada à pele usando dois ou mais eletrodos. Uma típica unidade TENS operada por bateria é capaz de modular a largura, frequência e intensidade de pulso.

#### Componentes 

- 2x 555;
- 1x 2N3053;
- 1x TIP122;
- 1x 7805;
- 1x Transformer 12V 100mA (~8:1);
- 2x 1N4004;
- Potenciometros: 10K ohm (2x) e 5K ohm (1x);
- Capacitores: 10uF (1x) e 100uF (1x);
- Resistores: 33K ohm (2x), 1K ohm (2x), 330 ohm (1x) e 220 ohm (4x);
- 3x LEDs.

#### Esquemático

O arquivo do esquemático em [Proteus](https://www.labcenter.com/) pode ser visto [aqui](https://github.com/leandcesar/emg-and-tens/blob/master/TENS).

![Esquemático do TENS](https://github.com/leandcesar/emg-and-tens/blob/master/TENS/TENS.png)

## Arduino (opcional)

Para obter melhores resultados, você pode usar um [Arduino](https://www.arduino.cc/) conectado entre a saída do EMG e a entrada do TENS.

```C++
#define EMG A0
#define TENS D2

void setup() {
  pinMode(EMG, INPUT);
  pinMode(TENS, OUTPUT);
}

void loop() {
  digitalWrite(TENS, (analogRead(EMG) > 512));
}
```

## Procedimento experimental

1. Coloque três eletrodos de superfície EMG próximos um do outro no antebraço.
2. Usando garras jacaré, conecte o eletrodo do meio ao terra do EMG e os outros dois eletrodos às entradas do EMG.
3. Coloque dois eletrodos de superfície EMG próximos um do outro no nervo ulnar.
4. Usando garras jacaré, conecte os eletrodos às saídas do TENS.
5. Comece com o dispositivo TENS na configuração mais baixa.
6. Lentamente, comece a aumentar a potência do dispositivo TENS até ver uma resposta.

**Importante:** se retirar os eletrodos antes que o dispositivo TENS seja desligado, o circuito ficará em curto-circuito e enviará estímulos constantemente. Evite isso! Para parar a experiência, primeiro desligue totalmente o dispositivo TENS.

**Nota**: uma unidade TENS por definição fornece corrente suficiente para causar contração muscular. Não coloque eletrodos nos músculos da garganta ou no peito.

## Agradecimentos

- [Backyard Brains](https://backyardbrains.com)
- [Meduag](https://www.youtube.com/user/meduag/)
- [Ex Machina Unifei](https://www.facebook.com/ExMachina.UNIFEI)

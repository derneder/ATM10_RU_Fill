---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: "Каналы"
  icon: controller
---

# Каналы

Для [МЭ-сетей](me-network-connections.md) Applied Energistics 2 нужны
каналы, чтобы поддерживать [устройства](../ae2-mechanics/devices.md), использующие сетевое хранилище, или другие сетевые
службы. Представьте каналы как USB-кабели ко всем вашим устройствам. У компьютера только столько USB-портов, и он может поддерживать
лишь столько подключённых устройств. Большинство машин, полноблочных устройств и стандартных кабелей могут пропускать не более
8 каналов. Полноблочные устройства и стандартные кабели можно представить как пучок из 8 «проводов каналов». Однако [непрозрачные кабели](../items-blocks-machines/cables.md#dense-cable) поддерживают до
32 каналов. Единственные другие устройства, способные передавать 32, — <ItemLink id="me_p2p_tunnel" />
и [квантовый сетевой мост](../items-blocks-machines/quantum_bridge.md). Каждый раз, когда устройство занимает канал, представьте, что из пучка выдёргивается USB-«провод»,
а значит, этот «провод» дальше по линии уже недоступен.

<GameScene zoom="7" interactive={true}>
  <ImportStructure src="../assets/assemblies/channel_demonstration_1.snbt" />

  <LineAnnotation color="#33ff33" from="1 .4 .7" to="2.4 .4 .7" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .6 .7" to="2.4 .6 .7" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .4 .6" to="2.6 .4 .6" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .6 .6" to="2.6 .6 .6" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .6 .6" to="2.6 .6 .6" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="2.4 .6 .7" to="2.4 .6 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.4 .4 .7" to="2.4 .4 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.6 .6 .6" to="2.6 .6 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.6 .4 .6" to="2.6 .4 1.5" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="2.1 .6 1.5" to="2.4 .6 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.6 .4 1.5" to="2.9 .4 1.5" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="2.6 .6 1.5" to="2.6 .9 1.5" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="2.4 .1 1.5" to="2.4 .4 1.5" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="1 .6 .4" to="3.5 .6 .4" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .4 .4" to="3.5 .4 .4" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="3.5 .6 .4" to="3.5 .9 .4" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="3.5 .1 .4" to="3.5 .4 .4" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="1 .6 .3" to="1.5 .6 .3" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1 .4 .3" to="1.5 .4 .3" alwaysOnTop={true}/>

  <LineAnnotation color="#33ff33" from="1.5 .6 .3" to="1.5 .9 .3" alwaysOnTop={true}/>
  <LineAnnotation color="#33ff33" from="1.5 .1 .3" to="1.5 .4 .3" alwaysOnTop={true}/>

  <LineAnnotation color="#ff3333" from="3.5 .5 .5" to="5.5 .5 .5" alwaysOnTop={true}>
  Все 8 каналов в кабеле заняты, поэтому накопитель не получает канал.  
  </LineAnnotation>

  <LineAnnotation color="#993333" from="1 .5 .5" to="1.25 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="1.5 .5 .5" to="1.75 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="2 .5 .5" to="2.25 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="2.5 .5 .5" to="2.75 .5 .5" alwaysOnTop={true}/>
  <LineAnnotation color="#993333" from="3 .5 .5" to="3.25 .5 .5" alwaysOnTop={true}/>

  <DiamondAnnotation pos="3.6 0.5 0.5" color="#ff0000">
        Все 8 каналов в кабеле заняты, поэтому накопитель не получает канал.
    </DiamondAnnotation>

  <IsometricCamera yaw="15" pitch="30" />
</GameScene>

Простой способ увидеть, как используются и направляются каналы в вашей сети, — [умные кабели](../items-blocks-machines/cables.md): на них отображаются пути и загрузка каналов.

Каналы потребляют 1⁄128 ae/t на каждый пройденный узел, а значит, если
добавить «<ItemLink id="controller" />» в
сеть с 8 устройствами и более чем 96 узлами, расход энергии может на самом деле
уменьшиться, потому что меняется распределение каналов.

Обратите внимание: **КАНАЛЫ НИКАК НЕ СВЯЗАНЫ С ЦВЕТОМ КАБЕЛЯ**, цвет кабеля лишь не даёт кабелям соединяться.

## Маршрутизация каналов

При использовании блока «<ItemLink id="controller" />»
каналы прокладываются в 3 шага. Сначала они идут кратчайшим путём через соседние машины к ближайшему [обычному кабелю](../items-blocks-machines/cables.md)
(стеклянному, покрытому или умному). Затем кратчайшим путём через этот обычный кабель к ближайшему [непрозрачному кабелю](../items-blocks-machines/cables.md)
(непрозрачному или непрозрачному умному). Затем кратчайшим путём через этот непрозрачный кабель к блоку «<ItemLink id="controller" />».
Если кратчайший путь уже загружен до предела, некоторые [устройства](devices.md) могут не получить нужные каналы; используйте
цветные кабели, кабельные якоря и тоннели, чтобы каналы шли по нужному вам пути.

Например, в этом случае некоторые накопители не получают каналы: хотя пропускной способности кабелей хватает,
каналы стремятся пройти кратчайшим путём, перегружая одни кабели и оставляя другие пустыми.

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/channel_path_length_issue.snbt" />

  <LineAnnotation color="#33ff33" from="3 .5 1.4" to="0.4 0.5 1.4" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 .5 1.4" to="0.4 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 0.5 3.6" to="1.4 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1.4 0.5 3.6" to="1.4 0.5 5" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#33ff33" from="3 0.5 3.6" to="1.6 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1.6 0.5 3.6" to="1.6 0.5 5" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#ff3333" from="3 .5 1.6" to="0.6 .5 1.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#ff3333" from="0.6 .5 1.6" to="0.6 .5 3.4" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#ff3333" from="0.6 .5 3.4" to="1.4 .5 3.4" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#ff3333" from="3 .5 3.4" to="1.6 .5 3.4" alwaysOnTop={true} thickness="0.05"/>

  <BoxAnnotation color="#dddddd" min="1.2 0.2 3.2" max="1.8 0.8 3.8" alwaysOnTop={true} thickness="0.05">
        Здесь пытаются пройти более 8 каналов, поэтому часть из них отсекается.
  </BoxAnnotation>

  <IsometricCamera yaw="90" pitch="90" />

</GameScene>

Это можно исправить, более тщательно ограничив пути, по которым могут идти каналы. Сети должны быть похожи на дерево (или куст).
Петель и неоднозначных путей каналов следует по возможности избегать.

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/channel_path_length_issue_fix.snbt" />

  <LineAnnotation color="#33ff33" from="3 .5 1.4" to="0.4 0.5 1.4" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 .5 1.4" to="0.4 0.5 5.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="0.4 0.5 5.6" to="1 0.5 5.6" alwaysOnTop={true} thickness="0.05"/>

  <LineAnnotation color="#33ff33" from="3 0.5 3.6" to="1.6 0.5 3.6" alwaysOnTop={true} thickness="0.05"/>
  <LineAnnotation color="#33ff33" from="1.6 0.5 3.6" to="1.6 0.5 5" alwaysOnTop={true} thickness="0.05"/>

  <IsometricCamera yaw="90" pitch="90" />

</GameScene>

## Ad-hoc сети

Сеть без блока «<ItemLink id="controller" />»
считается ad-hoc сетью и поддерживает до 8 устройств, использующих каналы.
Если устройств станет больше 8, использующие каналы устройства сети отключатся,
и тогда можно либо убрать устройства, либо добавить <ItemLink id="controller" />.

В отличие от сетей с контроллером, [умные кабели](../items-blocks-machines/cables.md) в ad-hoc сетях показывают число
используемых каналов по всей сети, а не число каналов, проходящих через конкретный кабель.

В ad-hoc сетях каждое устройство
использует 1 канал на всю сеть; это сильно отличается от того, как <ItemLink id="controller" /> распределяет каналы на основе
кратчайшего маршрута.

## Проектирование

Как упоминалось ранее в разделе о [маршрутизации каналов](channels.md#channel-routing), сеть лучше проектировать в виде дерева: непрозрачные кабели расходятся от контроллера, обычные кабели
расходятся от непрозрачных, а [устройства](../ae2-mechanics/devices.md) собраны в группы по 8 или меньше на обычных кабелях.

Вот пример того, как делать не стоит:

Проследим пути каналов:

1. Сразу справа от контроллера мы упираемся в ограничение в 8 каналов, потому что накопитель действует как обычный кабель.
Однако, поскольку здесь нет умного кабеля, мы не видим, сколько каналов используется. Осталось 8 каналов.
2. Накопитель занимает канал.
Осталось 7 каналов.
3. 2 канала уходят вверх к терминалам.
Осталось 5 каналов.
4. Идём дальше вправо: интерфейс занимает ещё один канал.
Осталось 4 канала.
5. 1 канал уходит вверх к поставщику шаблонов.
Осталось 3 канала.
6. Идём дальше вправо: 1 канал уходит вверх к шине импорта.
Осталось 2 канала.
7. Группа поставщиков шаблонов, питающих сборщики, получает только 2 канала, поэтому 2 поставщика остаются без каналов.

В итоге ошибка заключается в том, что каналы зажаты в узком месте и не продумано, как они будут распределяться.

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/bad_network_structure.snbt" />

<LineAnnotation color="#33ff33" from="6.5 .5 1.5" to="6 .5 1.5" alwaysOnTop={true} thickness="0.4">
  32 канала
</LineAnnotation>

<LineAnnotation color="#33ff33" from="6 .5 1.5" to="5.5 .5 1.5" alwaysOnTop={true} thickness="0.2">
  8 каналов
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 .5 1.5" to="5.5 1.5 1.5" alwaysOnTop={true} thickness="0.1">
  2 канала
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 .5 1.5" to="5.5 .3 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 1.5 1.5" to="5.5 2.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 2.5 1.5" to="5.5 2.5 1.1" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="5.5 .5 1.5" to="4.5 .5 1.5" alwaysOnTop={true} thickness="0.158">
  5 каналов
</LineAnnotation>

<LineAnnotation color="#33ff33" from="4.5 .5 1.5" to="4.5 .3 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="4.5 .5 1.5" to="4.5 1.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="4.5 .5 1.5" to="3.5 .5 1.5" alwaysOnTop={true} thickness="0.122">
  3 канала
</LineAnnotation>

<LineAnnotation color="#33ff33" from="3.5 .5 1.5" to="3.5 2.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="3.5 2.5 1.5" to="3.7 2.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="3.5 .5 1.5" to="1.5 .5 1.5" alwaysOnTop={true} thickness="0.1">
  2 канала
</LineAnnotation>

<LineAnnotation color="#33ff33" from="1.5 0.5 1.5" to="1.5 0.3 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="1.5 0.5 1.5" to="0.5 0.5 1.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#33ff33" from="0.5 0.5 1.5" to="0.5 0.5 0.5" alwaysOnTop={true} thickness="0.071">
  1 канал
</LineAnnotation>

<LineAnnotation color="#ff3333" from="0.5 1.5 1.5" to="0.5 1.3 1.5" alwaysOnTop={true} thickness="0.071">
  нет каналов
</LineAnnotation>

<LineAnnotation color="#ff3333" from="1.5 1.5 0.5" to="1.5 1.3 0.5" alwaysOnTop={true} thickness="0.071">
  нет каналов
</LineAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

---

Вот пример хорошей структуры:

<GameScene zoom="2.5" interactive={true}>
  <ImportStructure src="../assets/assemblies/treelike_network_structure.snbt" />

    <BoxAnnotation color="#dddddd" min="6.9 0 4.9" max="9.1 4 7.1" thickness="0.05">
        Обратите внимание: поставщики шаблонов разделены на отдельные группы по 8.
    </BoxAnnotation>

    <BoxAnnotation color="#dddddd" min="5 4 4" max="8 5 5" thickness="0.05">
        Когда сходятся два обычных кабеля, полных каналов, нужен непрозрачный кабель.
    </BoxAnnotation>

    <BoxAnnotation color="#dddddd" min="5 0 13" max="8 1 14" thickness="0.05">
        Разные цвета кабелей используются, чтобы соседние кабели не соединялись.
    </BoxAnnotation>


  <IsometricCamera yaw="315" pitch="30" />
</GameScene>

## Режимы каналов

AE2 10.0.0 для Minecraft 1.18 добавляет новые возможности менять поведение каналов AE2 в вашем мире.
В общем разделе конфигурации появился новый параметр (`channels`), управляющий этим, а также новая внутриигровая
команда для операторов, позволяющая сменить режим и конфигурацию прямо из игры. Команда `/ae2 channelmode <mode>`
меняет режим, а `/ae2 channelmode` показывает текущий режим. Когда режим меняется в игре, все существующие сети
перезагружаются и сразу начинают использовать новый режим.

Это возрождает и улучшает возможность, существовавшую в Minecraft 1.12, и добавляет более удачные варианты для
игроков, которым хочется чуть более расслабленной игры, но не хочется полностью убирать эту механику.

В таблице ниже перечислены доступные режимы, как в файле конфигурации, так и в команде.

| Настройка | Описание |
| --- | --- |
| `default` | Стандартный режим с пропускной способностью кабелей и ad-hoc сетей, как описано во всём этом руководстве |
| `x2` | Все пропускные способности каналов удвоены (16 на обычном кабеле, 64 на непрозрачном кабеле, ad-hoc сети поддерживают 16 каналов) |
| `x3` | Все пропускные способности каналов утроены (24 на обычном кабеле, 92 на непрозрачном кабеле, ad-hoc сети поддерживают 24 канала) |
| `x4` | Все пропускные способности каналов учетверены (32 на обычном кабеле, 128 на непрозрачном кабеле, ad-hoc сети поддерживают 32 канала) |
| `infinite` | Все ограничения каналов сняты. Контроллеры по-прежнему *значительно* снижают энергопотребление сетей. Умные кабели лишь переключаются между полностью выключенным состоянием (каналы не передаются) и полностью включённым (передаётся 1 канал или больше). |
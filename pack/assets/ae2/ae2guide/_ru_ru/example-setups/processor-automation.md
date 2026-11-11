---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Автоматизация процессоров"
  icon: logic_processor
---

# Автоматизация производства процессоров

Есть много способов автоматизировать производство [процессоров](../items-blocks-machines/processors.md), и это один из них.

Такую общую схему можно собрать с любыми трубами, кондуитами, каналами или как там их называет мод для логистики предметов, лишь бы
их можно было фильтровать.

![The Process FLow Diagram](../assets/diagrams/processor_flow_diagram.png)

Ниже подробно описано, как сделать это только средствами AE2 с помощью [подсетей-«труб»](pipe-subnet.md).

Учтите: раз здесь используется «<ItemLink id="pattern_provider" />», схема рассчитана на встраивание в вашу систему [автокрафта](../ae2-mechanics/autocrafting.md).
Если вы просто хотите автоматизировать процессоры отдельно, замените поставщик шаблонов ещё одной бочкой и кладите ингредиенты прямо в верхнюю бочку.

Заодно схема обратно совместима
с прежними версиями AE2: даже если высекатели «<ItemLink id="inscriber" />» работают только с определённых сторон, подсети-трубы всё равно вставляют предметы в нужные грани и
извлекают их из нужных.

## Урок по кодированию шаблонов

Нередко [шаблон](../items-blocks-machines/patterns.md), который нужно закодировать, **НЕ СОВПАДАЕТ С ТЕМ, ЧТО ВЫ ВИДИТЕ В JEI**, или с тем, что JEI выдаёт при нажатии кнопки «+».
В этом случае JEI создаст два отдельных шаблона: один для печатных деталей и один для финальной сборки, а шаблон
печатных деталей будет включать [пресс](../items-blocks-machines/presses.md). Нам это не нужно, потому что установка делает не это. Нам нужен один шаблон,
который принимает сырые ресурсы и выдаёт готовый процессор, а поскольку пресс уже находится в высекателе, класть его в шаблон не нужно.

---

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/processor_automation.snbt" />

  <BoxAnnotation color="#dddddd" min="5 1 0" max="6 2 1" thickness=".05">
        (1) Поставщик шаблонов: в конфигурации по умолчанию, с нужными шаблонами обработки.

        <Row>
            ![Logic Pattern](../assets/diagrams/logic_pattern_small.png)
            ![Calculation Pattern](../assets/diagrams/calculation_pattern_small.png)
            ![Engineering Pattern](../assets/diagrams/engineering_pattern_small.png)
        </Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4.7 2 0" max="5 3 1" thickness=".05">
        (2) Шина хранения №1: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 1 0" max="4.3 2 1" thickness=".05">
        (3) Шина экспорта №1: фильтр на кремний, 2 карты ускорения
        <Row><ItemImage id="silicon" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 4 0" max="4.3 3 1" thickness=".05">
        (4) Шина экспорта №2: фильтр на золотой слиток, 2 карты ускорения
        <Row><ItemImage id="minecraft:gold_ingot" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 5 0" max="4.3 4 1" thickness=".05">
        (5) Шина экспорта №3: фильтр на кристалл истинного кварца, 2 карты ускорения
        <Row><ItemImage id="certus_quartz_crystal" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 6 0" max="4.3 5 1" thickness=".05">
        (6) Шина экспорта №4: фильтр на алмаз, 2 карты ускорения
        <Row><ItemImage id="minecraft:diamond" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.3 3 0" max="2 2 1" thickness=".05">
        (7) Шина экспорта №5: фильтр на редстоуновую пыль, 2 карты ускорения
        <Row><ItemImage id="minecraft:redstone" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 1 0" max="3 2 1" thickness=".05">
        (8) Высекатель №1: в конфигурации по умолчанию. Установлены кремниевый пресс и 4 карты ускорения
        <Row><ItemImage id="silicon_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 3 0" max="3 4 1" thickness=".05">
        (9) Высекатель №2: в конфигурации по умолчанию. Установлены логический пресс и 4 карты ускорения
        <Row><ItemImage id="logic_processor_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 4 0" max="3 5 1" thickness=".05">
        (10) Высекатель №3: в конфигурации по умолчанию. Установлены вычислительный пресс и 4 карты ускорения
        <Row><ItemImage id="calculation_processor_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4 5 0" max="3 6 1" thickness=".05">
        (11) Высекатель №4: в конфигурации по умолчанию. Установлены инженерный пресс и 4 карты ускорения
        <Row><ItemImage id="engineering_processor_press" scale="2" /> <ItemImage id="speed_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 2 0" max="1 3 1" thickness=".05">
        (12) Высекатель №5: в конфигурации по умолчанию. Установлены 4 карты ускорения
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 2 0" max="3 1 1" thickness=".05">
        (13) Шина импорта №1: в конфигурации по умолчанию, 2 карты ускорения
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 4 0" max="3 3 1" thickness=".05">
        (14) Шина импорта №2: в конфигурации по умолчанию, 2 карты ускорения
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 5 0" max="3 4 1" thickness=".05">
        (15) Шина импорта №3: в конфигурации по умолчанию, 2 карты ускорения
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 6 0" max="3 5 1" thickness=".05">
        (16) Шина импорта №4: в конфигурации по умолчанию, 2 карты ускорения
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 3 0" max="1 3.3 1" thickness=".05">
        (17) Шина хранения №2: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 1.7 0" max="1 2 1" thickness=".05">
        (18) Шина хранения №3: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 2 0" max="0.7 3 1" thickness=".05">
        (19) Шина импорта №5: в конфигурации по умолчанию, 2 карты ускорения
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="5 0.7 0" max="6 1 1" thickness=".05">
        (20) Шина хранения №4: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.3 2.7 0.3" max="3.7 3 0.7" thickness=".05">
        Кварцевое волокно питает все 3 высекателя, потому что высекатели ведут себя как кабели и поэтому передают энергию
  </BoxAnnotation>

<DiamondAnnotation pos="7 1.5 0.5" color="#00ff00">
        В основную МЭ-сеть
    </DiamondAnnotation>

  <IsometricCamera yaw="185" pitch="5" />
</GameScene>

## Конфигурации

* <ItemLink id="pattern_provider" /> (1) находится в конфигурации по умолчанию, с нужными шаблонами «<ItemLink id="processing_pattern" />».
  Обратите внимание: шаблоны ведут напрямую от сырых ресурсов к готовому процессору и **НЕ** включают [пресс](../items-blocks-machines/presses.md).

  ![Logic Pattern](../assets/diagrams/logic_pattern.png)
  ![Calculation Pattern](../assets/diagrams/calculation_pattern.png)
  ![Engineering Pattern](../assets/diagrams/engineering_pattern.png)

* Шины хранения «<ItemLink id="storage_bus" />» (2, 17, 18, 20) находятся в конфигурации по умолчанию.
* Шины экспорта «<ItemLink id="export_bus" />» (3-7) настроены на нужный ингредиент. В них стоят 2 карты «<ItemLink id="speed_card" />».
    <Row>
      <ItemImage id="silicon" scale="2" />
      <ItemImage id="minecraft:gold_ingot" scale="2" />
      <ItemImage id="certus_quartz_crystal" scale="2" />
      <ItemImage id="minecraft:diamond" scale="2" />
      <ItemImage id="minecraft:redstone" scale="2" />
    </Row>
* Шины импорта «<ItemLink id="import_bus" />» (13-16, 19) находятся в конфигурации по умолчанию. В них стоят 2 карты «<ItemLink id="speed_card" />».
* Высекатели «<ItemLink id="inscriber" />» находятся в конфигурации по умолчанию. В них стоят нужный [пресс](../items-blocks-machines/presses.md)
   и 4 карты «<ItemLink id="speed_card" />».
   <Row>
     <ItemImage id="silicon_press" scale="2" />
     <ItemImage id="logic_processor_press" scale="2" />
     <ItemImage id="calculation_processor_press" scale="2" />
     <ItemImage id="engineering_processor_press" scale="2" />
   </Row>

## Как это работает

1. <ItemLink id="pattern_provider" /> подаёт ингредиенты в бочку.
2. Первая [подсеть-труба](pipe-subnet.md) (оранжевая) вытягивает из бочки кремний, редстоуновую пыль и ингредиент нужного процессора
   (золотой слиток, кристалл истинного кварца или алмаз) и кладёт их в нужный высекатель «<ItemLink id="inscriber" />».
3. Первые четыре высекателя «<ItemLink id="inscriber" />» делают «<ItemLink id="printed_silicon" />», а также «<ItemLink id="printed_logic_processor" />»,
   «<ItemLink id="printed_calculation_processor" />» или «<ItemLink id="printed_engineering_processor" />».
4. Вторая и третья [подсети-трубы](pipe-subnet.md) (зелёные) забирают печатные схемы из первых четырёх высекателей «<ItemLink id="inscriber" />»
    и кладут их в пятый, финальный сборочный высекатель «<ItemLink id="inscriber" />».
5. Пятый высекатель «<ItemLink id="inscriber" />» собирает [процессор](../items-blocks-machines/processors.md).
6. Четвёртая [подсеть-труба](pipe-subnet.md) (фиолетовая) кладёт процессор в поставщик шаблонов, возвращая его в основную МЭ-сеть.
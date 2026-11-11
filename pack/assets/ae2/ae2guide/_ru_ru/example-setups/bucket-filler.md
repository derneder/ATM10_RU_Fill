---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Наполнитель вёдер"
  icon: minecraft:water_bucket
---

# Наполнитель вёдер

Смотрите также: [Опустошитель вёдер](bucket-emptier.md).

Учтите: поскольку здесь используется <ItemLink id="pattern_provider" />, схема рассчитана на встраивание в вашу
систему [автокрафта](../ae2-mechanics/autocrafting.md).

Иногда жизнь неудобна: вам нужны вёдра с жидкостью, а не сама жидкость. Иногда с этим справляется какая-нибудь машина
(например, жидкостный транспозер из Thermal Expansion), но не всегда у вас есть мод, который делает это удобно. К счастью,
в ванильном Minecraft есть чуть менее удобный способ — <ItemLink id="minecraft:dispenser" />.

**Учтите: часто этого можно не делать, потому что «Замещение жидкости» в
[терминале для закодированных шаблонов](../items-blocks-machines/terminals.md#pattern-encoding-terminal) позволяет использовать в
рецепте саму жидкость вместо ведра.**

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/bucket_filler.snbt" />

<BoxAnnotation color="#dddddd" min="2 1 0" max="3 2 1">
        (1) Поставщик шаблонов: настроен на блокировку создания «С сигналом редстоуна», с соответствующими шаблонами обработки.

        <Row>
        ![Fill Pattern](../assets/diagrams/water_fill_pattern_small.png)
        ![Fill Pattern](../assets/diagrams/lava_fill_pattern_small.png)
        </Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 1.1 0.1" max="3.2 1.9 0.9">
        (2) Интерфейс: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.1 1.1 0.8" max="3.9 1.9 1">
        (3) Шина хранения №1: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="4.05 1.05 0.8" max="4.95 1.95 1">
        (4) Плоскость формирования: фильтр по чёрному списку вёдер, для этого используется карта-инвертер.
        <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.2 2 1.2" max="3.8 2.2 1.8">
        (5) Шина импорта: фильтр по чёрному списку вёдер, для этого используется карта-инвертер.
        <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2.1 2 0.1" max="2.9 2.2 0.9">
        (6) Шина хранения №2: в конфигурации по умолчанию.
  </BoxAnnotation>

<DiamondAnnotation pos="0 1.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="225" pitch="45" />
</GameScene>

## Конфигурации

* <ItemLink id="pattern_provider" /> (1) настроен на блокировку создания «С сигналом редстоуна», с соответствующими шаблонами «<ItemLink id="processing_pattern" />».
  
    ![Charger Pattern](../assets/diagrams/water_fill_pattern.png)
    ![Charger Pattern](../assets/diagrams/lava_fill_pattern.png)

* <ItemLink id="interface" /> (2) находится в конфигурации по умолчанию.
* Первая <ItemLink id="storage_bus" /> (3) находится в конфигурации по умолчанию.
* <ItemLink id="formation_plane" /> (4) настроена на фильтр по чёрному списку вёдер, для этого используется карта-инвертер.
  <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
* <ItemLink id="import_bus" /> (5) настроена на фильтр по чёрному списку вёдер, для этого используется карта-инвертер.
  <Row><ItemImage id="minecraft:bucket" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
* Вторая <ItemLink id="storage_bus" /> (6) находится в конфигурации по умолчанию.

## Как это работает

1. <ItemLink id="pattern_provider" /> проталкивает ингредиенты в <ItemLink id="interface" />.
   (На самом деле для оптимизации он проталкивает предметы напрямую через шину хранения и плоскость формирования, как будто они — продолжения граней поставщика. Сами предметы в интерфейс никогда не попадают.)
2. Благодаря механизмам, описанным в статье про [подсеть-трубу](pipe-subnet.md#providing-to-multiple-places) и в описании плоскости «<ItemLink id="formation_plane" />»,
   ведро оказывается в блоке «<ItemLink id="minecraft:dispenser" />», а жидкость размещается плоскостью формирования.
3. <ItemLink id="minecraft:comparator" /> обнаруживает ведро в раздатчике и поэтому одновременно подаёт на него сигнал и блокирует
   <ItemLink id="pattern_provider" />.
4. Раздатчик зачерпывает ведром жидкость, и теперь внутри него полное ведро.
5. <ItemLink id="import_bus" /> вытягивает полное ведро из раздатчика и через шину «<ItemLink id="storage_bus" />» помещает его
   в поставщик шаблонов, возвращая в основную МЭ-сеть.
6. Компаратор видит, что раздатчик пуст, и разблокирует поставщик.

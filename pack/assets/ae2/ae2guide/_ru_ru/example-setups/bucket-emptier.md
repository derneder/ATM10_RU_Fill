---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Опустошитель вёдер"
  icon: minecraft:bucket
---

# Опустошитель вёдер

Смотрите также: [Наполнитель вёдер](bucket-filler.md).

Учтите: поскольку здесь используется <ItemLink id="pattern_provider" />, схема рассчитана на встраивание в вашу
систему [автокрафта](../ae2-mechanics/autocrafting.md).

Иногда жизнь неудобна: вам нужна сама жидкость, а получить её можно только в ведре. Иногда с этим справляется какая-нибудь машина
(например, жидкостный транспозер из Thermal Expansion), но не всегда у вас есть мод, который делает это удобно. К счастью,
в ванильном Minecraft есть чуть менее удобный способ — <ItemLink id="minecraft:dispenser" />.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/bucket_emptier.snbt" />

<BoxAnnotation color="#dddddd" min="2 1 0" max="3 2 1">
        (1) Поставщик шаблонов: настроен на блокировку создания «С сигналом редстоуна», включён режим блокирования, с соответствующими шаблонами обработки.

        <Row>
        ![Fill Pattern](../assets/diagrams/water_empty_pattern_small.png)
        ![Fill Pattern](../assets/diagrams/lava_empty_pattern_small.png)
        </Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2.1 2 0.1" max="2.9 2.2 0.9">
        (2) Интерфейс: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.1 2 1.1" max="3.9 2.2 1.9">
        (3) Шина хранения №1: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="4.05 1.05 0.8" max="4.95 1.95 1">
        (4) Плоскость уничтожения: окна настройки нет.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.2 1.2 0.8" max="3.8 1.8 1">
        (5) Шина импорта: фильтр — вёдра.
        <ItemImage id="minecraft:bucket" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 1.1 0.1" max="3.2 1.9 0.9">
        (6) Шина хранения №2: в конфигурации по умолчанию.
  </BoxAnnotation>

<DiamondAnnotation pos="0 1.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="225" pitch="45" />
</GameScene>

## Конфигурации

* <ItemLink id="pattern_provider" /> (1) настроен на блокировку создания «С сигналом редстоуна», режим блокирования включён,
  с соответствующими шаблонами «<ItemLink id="processing_pattern" />».
  
    ![Charger Pattern](../assets/diagrams/water_empty_pattern.png)
    ![Charger Pattern](../assets/diagrams/lava_empty_pattern.png)

* <ItemLink id="interface" /> (2) находится в конфигурации по умолчанию.
* Первая <ItemLink id="storage_bus" /> (3) находится в конфигурации по умолчанию.
* <ItemLink id="annihilation_plane" /> (4) не имеет окна настройки и не настраивается.
* <ItemLink id="import_bus" /> (5) настроена на фильтрацию по вёдрам.
  <ItemImage id="minecraft:bucket" scale="2" />
* Вторая <ItemLink id="storage_bus" /> (6) находится в конфигурации по умолчанию.

## Как это работает

1. <ItemLink id="pattern_provider" /> проталкивает ингредиенты в <ItemLink id="interface" />.
   (На самом деле для оптимизации он проталкивает предметы напрямую через шину хранения, как будто она — продолжение граней поставщика. Сами предметы в интерфейс никогда не попадают.)
2. Благодаря механизмам, описанным в статье про [подсеть-трубу](pipe-subnet.md#providing-to-multiple-places),
   ведро оказывается в блоке «<ItemLink id="minecraft:dispenser" />».
3. <ItemLink id="minecraft:comparator" /> обнаруживает ведро в раздатчике и поэтому одновременно подаёт на него сигнал и блокирует
   <ItemLink id="pattern_provider" />.
4. Раздатчик выливает жидкость из ведра, и теперь внутри него пустое ведро.
5. <ItemLink id="import_bus" /> вытягивает пустое ведро из раздатчика и через шину «<ItemLink id="storage_bus" />» помещает его
   в поставщик шаблонов, возвращая в основную МЭ-сеть.
6. Компаратор видит, что раздатчик пуст, и разблокирует поставщик.
---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Автоматизация печи"
  icon: minecraft:furnace
---

# Автоматизация печи

Учтите: поскольку здесь используется <ItemLink id="pattern_provider" />, схема рассчитана на встраивание в вашу
систему [автокрафта](../ae2-mechanics/autocrafting.md). Если вам нужно просто автоматизировать печь отдельно, используйте воронки, сундуки и тому подобное.

Автоматизировать <ItemLink id="minecraft:furnace" /> чуть сложнее, чем более простые механизмы вроде [зарядника](../example-setups/charger-automation.md).
Печи нужен ввод с двух разных сторон и вывод с третьей. Плавящийся предмет нужно вставлять через верхнюю грань,
топливо — через боковую, а результат забирать снизу. 

Для этого можно использовать: сверху — <ItemLink id="pattern_provider" />,
сбоку — <ItemLink id="export_bus" /> для постоянной подачи топлива, а снизу — <ItemLink id="import_bus" />
для импорта результатов в сеть. Однако при этом тратятся 3 [канала](../ae2-mechanics/channels.md).

Вот как это можно сделать всего с 1 каналом:

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/furnace_automation.snbt" />

<BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) Поставщик шаблонов: направленный вариант (получается при использовании гаечного ключа из истинного кварца), с соответствующими шаблонами обработки.

        ![Iron Pattern](../assets/diagrams/furnace_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 1.3 1">
        (2) Интерфейс: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="1.3 2 1">
        (3) Шина хранения №1: фильтр — уголь.
        <ItemImage id="minecraft:coal" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 2 0" max="1 2.3 1">
        (4) Шина хранения №2: фильтр по чёрному списку с углём, для этого используется карта-инвертер.
        <Row><ItemImage id="minecraft:coal" scale="2" /><ItemImage id="inverter_card" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

* <ItemLink id="pattern_provider" /> (1) находится в конфигурации по умолчанию, с соответствующими шаблонами «<ItemLink id="processing_pattern" />».
    Чтобы сделать его направленным, используйте на нём <ItemLink id="certus_quartz_wrench" />.

  ![Iron Pattern](../assets/diagrams/furnace_pattern.png)

* <ItemLink id="interface" /> (2) находится в конфигурации по умолчанию.
* Первая <ItemLink id="storage_bus" /> (3) настроена на фильтрацию по углю или по любому другому топливу, которое вы хотите использовать.
* Вторая <ItemLink id="storage_bus" /> (4) настроена на фильтр по чёрному списку с используемым вами топливом; для этого используется <ItemLink id="inverter_card" />.

## Как это работает

1. <ItemLink id="pattern_provider" /> проталкивает ингредиенты в <ItemLink id="interface" />.
   (На самом деле для оптимизации он проталкивает предметы напрямую через шины хранения, как будто они — продолжения граней поставщика. Сами предметы в интерфейс никогда не попадают.)
2. Интерфейс настроен так, чтобы ничего не хранить, поэтому он пытается протолкнуть ингредиенты в [сетевое хранилище](../ae2-mechanics/import-export-storage.md).
3. Единственные хранилища в зелёной подсети — шины «<ItemLink id="storage_bus" />». Шина с фильтром по углю помещает уголь в слот топлива печи через боковую грань.
    Шина с фильтром «не уголь» помещает плавящиеся предметы в верхний слот через верхнюю грань.
4. Печь делает своё печное дело.
5. Воронка вытягивает результаты снизу печи и кладёт их в слоты возврата поставщика, возвращая их в основную МЭ-сеть.

---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Автоматизация бросания в воду"
  icon: fluix_crystal
---

# Автоматизация рецептов с бросанием в воду

Обратите внимание: поскольку здесь используется «<ItemLink id="pattern_provider" />», эта схема рассчитана на интеграцию
в вашу систему [автокрафта](../ae2-mechanics/autocrafting.md).

Некоторые рецепты требуют бросить предметы в воду (похожая схема подойдёт и для бросания предметов в другие места).
Это можно автоматизировать с помощью «<ItemLink id="formation_plane" />», «<ItemLink id="annihilation_plane" />»
и вспомогательной инфраструктуры (по сути это две модифицированные [подсети-«трубы»](pipe-subnet.md)).

Эту схему предполагается использовать вместе с [автоматизацией зарядника](charger-automation.md), чтобы получать
«<ItemLink id="charged_certus_quartz_crystal" />».

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/throw_in_water.snbt" />

<BoxAnnotation color="#dddddd" min="2 0 1" max="3 1 2">
        (1) Поставщик шаблонов: в конфигурации по умолчанию, с нужными обрабатывающими шаблонами.

        ![Fluix Pattern](../assets/diagrams/fluix_pattern_small.png) ![Flawed Budding Pattern](../assets/diagrams/flawed_budding_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1.7 0 1" max="2 1 2">
        (2) Интерфейс: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 .7 1" max="2 1 2">
        (3) Плоскость формирования: настроена выбрасывать входные предметы как предметы.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 2 1" max="2 2.3 2">
        (4) Плоскость уничтожения: окна настройки нет.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 1 1" max="3 1.3 2">
        (5) Шина хранения: разметка на выходы шаблонов.
        <Row><ItemImage id="fluix_crystal" scale="2" /><BlockImage id="flawless_budding_quartz" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="3.9 0.5 1.5" color="#00ff00">
        В основную сеть и к автоматизации зарядника
        <GameScene zoom="3" background="transparent">
          <ImportStructure src="../assets/assemblies/charger_automation.snbt" />
          <IsometricCamera yaw="195" pitch="30" />
        </GameScene>
    </DiamondAnnotation>

  <IsometricCamera yaw="180" pitch="0" />
</GameScene>

## Конфигурации и шаблоны

* «<ItemLink id="pattern_provider" />» (1) находится в конфигурации по умолчанию, с нужными «<ItemLink id="processing_pattern" />»
  * Для «<ItemLink id="fluix_crystal" />» отлично подходит стандартный рецепт из JEI/REI:

    ![Fluix Pattern](../assets/diagrams/fluix_pattern.png)

  * Для «<ItemLink id="flawed_budding_quartz" />», вероятно, лучше делать его сразу из «<ItemLink id="quartz_block" />»,
    чтобы избежать проблемы, когда вход одного рецепта является выходом другого, из-за чего шине хранения не удаётся задать разметку:

    ![Flawed Budding Pattern](../assets/diagrams/flawed_budding_pattern.png)

* «<ItemLink id="interface" />» (2) находится в конфигурации по умолчанию.
* «<ItemLink id="formation_plane" />» (3) настроена выбрасывать входные предметы как предметы.
* «<ItemLink id="annihilation_plane" />» (4) не имеет окна настройки и не может быть настроена.
* «<ItemLink id="storage_bus" />» (5) размечена на выходы шаблонов.

## Как это работает

1.  «<ItemLink id="pattern_provider" />» выталкивает ингредиенты в расположенный сбоку «<ItemLink id="interface" />» в зелёной подсети
2.  Интерфейс (поскольку по умолчанию не хранит ничего) пытается вытолкнуть своё содержимое в [сетевое хранилище](../ae2-mechanics/import-export-storage.md)
3.  Единственное хранилище в зелёной подсети — «<ItemLink id="formation_plane" />», которая выбрасывает получаемые предметы в воду
4.  «<ItemLink id="annihilation_plane" />» в оранжевой подсети пытается подобрать только что выброшенные предметы, но не может, потому что
    «<ItemLink id="storage_bus" />» сверху поставщика шаблонов (единственное хранилище в оранжевой подсети) размечена только на результаты возможных крафтов
5.  Предметы выполняют своё превращение в мире.
6.  Теперь плоскость уничтожения может подобрать предметы перед собой, так как шине хранения разрешено их хранить.
7.  Шина хранения помещает полученные предметы в поставщик шаблонов, возвращая их в сеть.

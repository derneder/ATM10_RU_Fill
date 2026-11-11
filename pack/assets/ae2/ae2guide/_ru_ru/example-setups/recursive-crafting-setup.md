---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Рекурсивное изготовление"
  icon: minecraft:netherite_upgrade_smithing_template
---

# Схема рекурсивного изготовления

Как сказано в разделе об [автокрафте](../ae2-mechanics/autocrafting.md), алгоритм планирования автокрафта не справляется с рецептами,
в которых основной результат — один из ингредиентов. Например, он не умеет клонировать шаблоны улучшения незерита «<ItemLink id="minecraft:netherite_upgrade_smithing_template" />».

Одно из решений — использовать способность «<ItemLink id="level_emitter" />» притворяться [шаблоном](../items-blocks-machines/patterns.md).

Затем он будет включать небольшую установку, которая постоянно выполняет изготовление. Здесь мы рассмотрим установку
для клонирования шаблонов улучшения незерита «<ItemLink id="minecraft:netherite_upgrade_smithing_template" />».

<RecipeFor id="minecraft:netherite_upgrade_smithing_template" />

***

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/recursive_recipe_setup.snbt" />

  <BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) Интерфейс: настроен на запас нужных дополнительных ингредиентов: алмаза и незерака.
        <Row><ItemImage id="minecraft:diamond" scale="2" /> <ItemImage id="minecraft:netherrack" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.3 1 0.3" max="2.7 1.3 0.7">
        (2) Излучатель уровня: настроен на «кузнечный шаблон улучшения незерита», режим «Излучать сигнал красного камня для изготовления предмета».
        <Row><ItemImage id="minecraft:netherite_upgrade_smithing_template" scale="2" /> <ItemImage id="crafting_card" scale="2" /></Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 0 0" max="2.3 1 1">
        (3) Шина импорта №1: фильтр на предметы, которые хранит в запасе интерфейс. Установлена редстоуновая карта. Режим красного камня:
        «Активируется сигналом».
        <Row>
        <ItemImage id="minecraft:diamond" scale="2" />
        <ItemImage id="minecraft:netherrack" scale="2" />
        <ItemImage id="redstone_card" scale="2" />
        </Row>
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 1" max="4 1.3 2">
        (4) Шина хранения №1: приоритет выше, чем у другой шины хранения. ОЧЕНЬ ВАЖНО.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 0 1" max="4 1 2">
        (5) Молекулярный сборщик: в нём лежит шаблон для дублирования кузнечного шаблона.

        ![Pattern](../assets/diagrams/smithing_template_pattern_small.png)

        Кроме того, при постройке схемы в него нужно сразу вручную вставить один кузнечный шаблон.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 0 1" max="3 1 2">
        (6) Шина импорта №2: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 0 1" max="2 1 1.3">
        (7) Шина хранения №2: фильтр на «кузнечный шаблон улучшения незерита». Приоритет ниже, чем у другой шины хранения.
        <ItemImage id="minecraft:netherite_upgrade_smithing_template" scale="2" />
  </BoxAnnotation>

<DiamondAnnotation pos="0 0.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="15" pitch="30" />
</GameScene>

## Конфигурации

* <ItemLink id="interface" /> (1) настроен на запас нужных дополнительных ингредиентов: алмаза и незерака.
* <ItemLink id="level_emitter" /> (2) настроен на «кузнечный шаблон улучшения незерита» и работает в режиме «Излучать сигнал красного камня для изготовления предмета».
* Первая шина импорта «<ItemLink id="import_bus" />» (3) настроена на предметы, которые хранит в запасе интерфейс. В ней стоит редстоуновая карта, режим красного камня — «Активируется сигналом».
* У первой шины хранения «<ItemLink id="storage_bus" />» (4) *более высокий* [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чем у второй шины хранения.
* В «<ItemLink id="molecular_assembler" />» (5) лежит шаблон для дублирования кузнечного шаблона, и в него уже вручную вставлен один кузнечный шаблон.

  ![Pattern](../assets/diagrams/smithing_template_pattern.png)

* Вторая шина импорта «<ItemLink id="import_bus" />» (6) находится в конфигурации по умолчанию.
* Вторая шина хранения «<ItemLink id="storage_bus" />» (7) настроена на «кузнечный шаблон улучшения незерита». Её [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority) *ниже*, чем у первой шины хранения.

## Как это работает

1. <ItemLink id="level_emitter" /> притворяется [шаблоном](../items-blocks-machines/patterns.md) благодаря вставленной
   «<ItemLink id="crafting_card" />» и режиму «Излучать сигнал красного камня для изготовления предмета». Поэтому «кузнечный шаблон улучшения незерита» появляется в
   [терминалах](../items-blocks-machines/terminals.md) как допустимая цель для [автокрафта](../ae2-mechanics/autocrafting.md).
2. Получив запрос на изготовление этого предмета — от игрока или от самой системы, — излучатель уровня включается.
3. Первая шина импорта «<ItemLink id="import_bus" />» активируется излучателем уровня и вытягивает ингредиенты, хранящиеся в запасе в «<ItemLink id="interface" />».
4. Единственная шина хранения «<ItemLink id="storage_bus" />» в сети, способная хранить эти ингредиенты, — та, что стоит на сборщике.
5. <ItemLink id="molecular_assembler" /> получает ингредиенты (в нём уже лежит 1 кузнечный шаблон) и выполняет изготовление, получая 2 кузнечных шаблона.
6. Вторая шина импорта «<ItemLink id="import_bus" />» извлекает 1 кузнечный шаблон.
7. У первой шины хранения приоритет выше, поэтому этот кузнечный шаблон возвращается в сборщик.
8. Вторая шина импорта «<ItemLink id="import_bus" />» извлекает ещё 1 кузнечный шаблон.
9. Сборщик не может принять ещё один кузнечный шаблон, поэтому второй кузнечный шаблон попадает в шину хранения с более низким приоритетом и вставляется в интерфейс.
10. <ItemLink id="interface" />, не настроенный на запас кузнечных шаблонов, передаёт его в сеть.
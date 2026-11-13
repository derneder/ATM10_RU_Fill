---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Ячейки хранения"
  icon: item_storage_cell_1k
  position: 410
categories:
- tools
item_ids:
- ae2:item_cell_housing
- ae2:fluid_cell_housing
- ae2:cell_component_1k
- ae2:cell_component_4k
- ae2:cell_component_16k
- ae2:cell_component_64k
- ae2:cell_component_256k
- ae2:item_storage_cell_1k
- ae2:item_storage_cell_4k
- ae2:item_storage_cell_16k
- ae2:item_storage_cell_64k
- ae2:item_storage_cell_256k
- ae2:fluid_storage_cell_1k
- ae2:fluid_storage_cell_4k
- ae2:fluid_storage_cell_16k
- ae2:fluid_storage_cell_64k
- ae2:fluid_storage_cell_256k
---

# Ячейки хранения

<Column>
  <Row>
    <ItemImage id="item_storage_cell_1k" scale="4" />

    <ItemImage id="item_storage_cell_4k" scale="4" />

    <ItemImage id="item_storage_cell_16k" scale="4" />

    <ItemImage id="item_storage_cell_64k" scale="4" />

    <ItemImage id="item_storage_cell_256k" scale="4" />
  </Row>

  <Row>
    <ItemImage id="fluid_storage_cell_1k" scale="4" />

    <ItemImage id="fluid_storage_cell_4k" scale="4" />

    <ItemImage id="fluid_storage_cell_16k" scale="4" />

    <ItemImage id="fluid_storage_cell_64k" scale="4" />

    <ItemImage id="fluid_storage_cell_256k" scale="4" />
  </Row>
</Column>

Ячейки хранения — один из основных способов хранения в Applied Energistics. Они вставляются в <ItemLink id="drive" />
или <ItemLink id="chest" />.

См. [Байты и типы](../ae2-mechanics/bytes-and-types.md) — там объясняется их вместимость в байтах и типах.

Компонент хранения можно извлечь из корпуса, если ячейка пуста: зажмите Shift и щёлкните правой кнопкой мыши, держа ячейку в руке.

<Row>
    <Recipe id="upgrade/item_storage_cell_1k_to_4k" />

    Ячейки хранения можно улучшать до более высоких уровней, комбинируя их с компонентами хранения более высокого уровня в сетке крафта. Содержимое при этом сохраняется, а компонент более низкого уровня возвращается.
</Row>

## Вместимость хранения при разном числе типов

[Начальная стоимость типов](../ae2-mechanics/bytes-and-types.md) такова, что ячейка с 1 типом вмещает вдвое больше, чем ячейка со всеми 63 используемыми типами.

| Ячейка                                   | Общая вместимость ячейки с 1 используемым типом | Общая вместимость ячейки с 63 используемыми типами |
| ---------------------------------------- | ----------------------------------------: | ------------------------------------------: |
| <ItemLink id="item_storage_cell_1k" />   |                                     8 128 |                                       4 160 |
| <ItemLink id="item_storage_cell_4k" />   |                                    32 512 |                                      16 640 |
| <ItemLink id="item_storage_cell_16k" />  |                                   130 048 |                                      66 560 |
| <ItemLink id="item_storage_cell_64k" />  |                                   520 192 |                                     266 240 |
| <ItemLink id="item_storage_cell_256k" /> |                                 2 080 768 |                                   1 064 960 |


## Задание фильтра

Ячейки можно фильтровать так, чтобы они принимали только определённые предметы, — по тому же принципу, что и <ItemLink id="storage_bus" />. Делается это на <ItemLink id="cell_workbench" />.

Предметы можно перетаскивать в слоты из JEI/REI, даже если их у вас на самом деле нет.

## Улучшения

Ячейки хранения поддерживают следующие [карты улучшений](upgrade_cards.md), вставляемые через <ItemLink id="cell_workbench" />:

*   <ItemLink id="fuzzy_card" /> (недоступна для жидкостных ячеек) позволяет задать фильтр по уровню повреждения и/или игнорировать NBT предмета
*   <ItemLink id="inverter_card" /> переключает фильтр с белого списка на чёрный
*   <ItemLink id="equal_distribution_card" /> выделяет каждому типу одинаковую долю байтов ячейки, чтобы один тип не мог заполнить её целиком
*   <ItemLink id="void_card" /> уничтожает вставляемые предметы, если ячейка заполнена (или если заполнена выделенная этому типу секция в случае с картой равномерного распределения) — полезно, чтобы фермы не забивались. Позаботьтесь о фильтре!
*   Переносные ячейки могут принимать <ItemLink id="energy_card" />, чтобы увеличить ёмкость их батареи

## Покраска

Переносные предметные и жидкостные ячейки можно красить так же, как кожаную броню, — скрафтив их вместе с красителями.

# Корпуса

Ячейки можно изготовить из компонента хранения и корпуса, либо по рецепту корпуса вокруг компонента хранения:

<Row>
  <Recipe id="network/cells/item_storage_cell_1k" />

  <Recipe id="network/cells/item_storage_cell_1k_storage" />
</Row>

Корпуса сами по себе крафтятся так:

<Row>
  <RecipeFor id="item_cell_housing" />

  <RecipeFor id="fluid_cell_housing" />
</Row>

# Компоненты хранения

Компоненты хранения — основа всех ячеек AE2: именно они определяют вместимость ячеек. Каждый уровень увеличивает вместимость
в 4 раза и стоит 3 компонента предыдущего уровня.

<Column>
  <Row>
    <RecipeFor id="cell_component_1k" />

    <RecipeFor id="cell_component_4k" />

    <RecipeFor id="cell_component_16k" />
  </Row>

  <Row>
    <RecipeFor id="cell_component_64k" />

    <RecipeFor id="cell_component_256k" />
  </Row>
</Column>

# Предметные ячейки хранения

Предметные ячейки хранения вмещают до 63 различных типов предметов и доступны во всех стандартных вариантах вместимости.

<Column>
  <Row>
    <Recipe id="network/cells/item_storage_cell_1k_storage" />

    <Recipe id="network/cells/item_storage_cell_4k_storage" />

    <Recipe id="network/cells/item_storage_cell_16k_storage" />
  </Row>

  <Row>
    <Recipe id="network/cells/item_storage_cell_64k_storage" />

    <Recipe id="network/cells/item_storage_cell_256k_storage" />
  </Row>
</Column>

## Переносное предметное хранилище

Работает как крошечный <ItemLink id="chest" /> в кармане — или как разновидность рюкзака. Заряжается в <ItemLink id="charger" />

В отличие от стандартных ячеек хранения, их вместимость по типам с ростом вместимости в байтах фактически *снижается*, а общая вместимость в байтах вдвое меньше.

Помимо карт улучшений, которые принимают все ячейки, они также принимают <ItemLink id="energy_card" /> для улучшения встроенных батарей.

<Column>
  <Row>
    <RecipeFor id="portable_item_cell_1k" />

    <RecipeFor id="portable_item_cell_4k" />

    <RecipeFor id="portable_item_cell_16k" />
  </Row>

  <Row>
    <RecipeFor id="portable_item_cell_64k" />

    <RecipeFor id="portable_item_cell_256k" />
  </Row>
</Column>

# Жидкостные ячейки хранения

Жидкостные ячейки хранения вмещают до 5 различных типов жидкостей и доступны во всех стандартных вариантах вместимости.

<Column>
  <Row>
    <Recipe id="network/cells/fluid_storage_cell_1k_storage" />

    <Recipe id="network/cells/fluid_storage_cell_4k_storage" />

    <Recipe id="network/cells/fluid_storage_cell_16k_storage" />
  </Row>

  <Row>
    <Recipe id="network/cells/fluid_storage_cell_64k_storage" />

    <Recipe id="network/cells/fluid_storage_cell_256k_storage" />
  </Row>
</Column>

## Переносное жидкостное хранилище

Работает как крошечный <ItemLink id="chest" /> в кармане — или как разновидность рюкзака. Заряжается в <ItemLink id="charger" />

В отличие от стандартных ячеек хранения, их вместимость по типам с ростом вместимости в байтах фактически *снижается*, а общая вместимость в байтах вдвое меньше.

Помимо карт улучшений, которые принимают все ячейки, они также принимают <ItemLink id="energy_card" /> для улучшения встроенных батарей.

<Column>
  <Row>
    <RecipeFor id="portable_fluid_cell_1k" />

    <RecipeFor id="portable_fluid_cell_4k" />

    <RecipeFor id="portable_fluid_cell_16k" />
  </Row>

  <Row>
    <RecipeFor id="portable_fluid_cell_64k" />

    <RecipeFor id="portable_fluid_cell_256k" />
  </Row>
</Column>

# Творческая ячейка хранения

<Row>
  <ItemImage id="creative_storage_cell" scale="2" />
</Row>

Творческие ячейки **не дают бесконечное хранилище**. Вместо этого они работают как бесконечный источник и бесконечный приёмник того
предмета или жидкости, [заданного в их фильтре](cell_workbench.md).

---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Процессоры"
  icon: logic_processor
  position: 010
categories:
- misc ingredients blocks
item_ids:
- ae2:logic_processor
- ae2:calculation_processor
- ae2:engineering_processor
- ae2:printed_silicon
- ae2:printed_logic_processor
- ae2:printed_calculation_processor
- ae2:printed_engineering_processor
- ae2:silicon
---

# Процессоры

<Row>
  <ItemImage id="logic_processor" scale="4" />

  <ItemImage id="calculation_processor" scale="4" />

  <ItemImage id="engineering_processor" scale="4" />
</Row>

Процессоры — один из основных ингредиентов в [устройствах](../ae2-mechanics/devices.md) и машинах AE2.
Также это одна из первых серьёзных задач для автоматизации. Существует три типа процессоров: изготавливаемые
соответственно с золотом, <ItemLink id="certus_quartz_crystal" /> и алмазом. Они создаются с помощью
[прессов](presses.md) во <ItemLink id="inscriber" /> в многоэтапном процессе (обычно реализуемом
цепочкой высекателей и фильтрующих труб).

## Этапы производства

<Column gap="5">
  1.  Соберите/изготовьте нужные ингредиенты: кремний, редстоун, золото, <ItemLink id="certus_quartz_crystal" />, алмаз.

  <RecipeFor id="silicon" />

  <br />

  2.  Отштампуйте необходимые печатные схемы

  <Row>
    <RecipeFor id="printed_silicon" />

    <RecipeFor id="printed_logic_processor" />
  </Row>

  <Row>
    <RecipeFor id="printed_calculation_processor" />

    <RecipeFor id="printed_engineering_processor" />
  </Row>

  <br />

  3.  Финальная сборка

  <Row>
    <RecipeFor id="logic_processor" />

    <RecipeFor id="calculation_processor" />
  </Row>

  <RecipeFor id="engineering_processor" />
</Column>

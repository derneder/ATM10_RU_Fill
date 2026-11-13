---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Приёмщик энергии"
  icon: energy_acceptor
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:energy_acceptor
---

# Приёмщик энергии

<Row gap="20">
<BlockImage id="energy_acceptor" scale="8" /> 

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/cable_energy_acceptor.snbt" />
</GameScene>
</Row>

Приёмщик энергии преобразует распространённые виды энергии из других технических модов во внутреннюю форму [энергии](../ae2-mechanics/energy.md) AE2 —
AE. Хотя «<ItemLink id="controller" />» тоже умеет это делать, грани контроллера слишком ценны, чтобы тратить их на это, поэтому часто лучше использовать именно приёмщик энергии.

Коэффициенты преобразования Forge Energy и TechReborn Energy таковы:

*   2 FE = 1 AE (Forge)
*   1 E  = 2 AE (Fabric)

Скорость преобразования полностью зависит от того, сколько AE способна хранить ваша сеть; причины объясняются
[на этой странице](../ae2-mechanics/energy.md).

## Варианты

Приёмщик энергии существует в 2 вариантах: обычном и плоском/[части кабеля](../ae2-mechanics/cable-subparts.md). Это позволяет делать некоторые сборки компактнее.

Обычный и плоский приёмщики энергии можно менять местами в сетке крафта.

## Рецепт

<RecipeFor id="energy_acceptor" />

<RecipeFor id="cable_energy_acceptor" />

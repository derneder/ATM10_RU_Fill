---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Фасады"
  icon: facade
  icon_components:
    "ae2:facade_item": "minecraft:stone"
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:facade
---

# Фасады

Фасады помогают придать базе более опрятный вид. Ими можно скрывать кабели обоих видов — обычные и плотные, а изготавливать их можно из самых разных блоков.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/facades_1.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Они могут закрывать все стороны кабеля, но при этом пропускать [части кабеля](../ae2-mechanics/cable-subparts.md) и кабельные соединения.

<GameScene zoom="6"  interactive={true}>
  <ImportStructure src="../assets/assemblies/facades_2.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Используйте их с умом, чтобы улучшить эстетику базы или сделать блоки с разной текстурой на каждой стороне.

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/facades_3.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Скрытие фасадов

Фасады скрываются, пока в любой из рук удерживается <a href="network_tool.md">сетевой инструмент</a>.

Можно взаимодействовать с блоками за скрытыми фасадами, не снимая фасады.

## Рецепт

Поместите блок, текстуру которого хотите получить, в центр из 4 «<ItemLink id="cable_anchor" />».

![Рецепт фасада](../assets/diagrams/facade_recipe.png)

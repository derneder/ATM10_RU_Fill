---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Молекулярный сборщик"
  icon: molecular_assembler
  position: 310
categories:
- machines
item_ids:
- ae2:molecular_assembler
---

# Молекулярный сборщик

<BlockImage id="molecular_assembler" scale="8" />

Молекулярный сборщик принимает помещённые в него предметы и выполняет операцию, заданную соседним <ItemLink id="pattern_provider" />
или вставленным <ItemLink id="crafting_pattern" />, <ItemLink id="smithing_table_pattern" /> либо <ItemLink id="stonecutting_pattern" />,
после чего выталкивает результат в соседние контейнеры.

В этом сборщике находится шаблон изготовления с рецептом «1 дубовое бревно = 4 дубовые доски». Когда дубовые бревна подаются в верхнюю воронку,
сборщик изготавливает доски и выбрасывает их в нижнюю воронку.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/standalone_assembler.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Основное применение молекулярного сборщика

Однако основное их применение — стоять рядом с <ItemLink id="pattern_provider" />. В этом случае поставщики шаблонов ведут себя особым образом
и отправляют информацию о соответствующем шаблоне вместе с ингредиентами в соседние сборщики. Поскольку сборщики сами выталкивают результаты
работы в соседние контейнеры (а значит, в возвратные слоты поставщика шаблонов), сборщик у поставщика шаблонов —
это всё, что нужно для автоматизации изготовления по шаблонам.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/assembler_tower.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Улучшения

Молекулярный сборщик поддерживает следующие [улучшения](upgrade_cards.md):

*   <ItemLink id="speed_card" />

## Рецепт

<RecipeFor id="molecular_assembler" />

## Примечание

Optifine ломает функцию «выталкивания в соседние контейнеры», поэтому большинство схем изготовления со сборщиками работать не будут.

---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Шина переключения"
  icon: toggle_bus
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:toggle_bus
- ae2:inverted_toggle_bus
---

# Шина переключения

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/assemblies/toggle_bus.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

Шина, работающая похоже на <ItemLink id="fluix_glass_cable" /> или другие кабели, но позволяющая переключать
состояние соединения сигналом редстоуна. Так можно отрезать участок [МЭ-сети](../ae2-mechanics/me-network-connections.md).

Когда подан сигнал редстоуна, часть включает соединение; <ItemLink id="inverted_toggle_bus" /> ведёт себя наоборот —
отключает его.

Стоит учесть: переключение этих частей может вызвать перезагрузку сети и пересчёт подключённых устройств.

Они являются [частями кабеля](../ae2-mechanics/cable-subparts.md).

## Рецепты

<RecipeFor id="toggle_bus" />

<RecipeFor id="inverted_toggle_bus" />

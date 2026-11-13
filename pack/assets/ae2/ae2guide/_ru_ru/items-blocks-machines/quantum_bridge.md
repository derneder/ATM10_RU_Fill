---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Квантовый мост"
  icon: quantum_ring
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:quantum_link
- ae2:quantum_ring
---

# Квантовый сетевой мост

![Сформированный квантовый сетевой мост](../assets/diagrams/quantum_bridge_demonstration.png)

Квантовые сетевые мосты могут расширять [сеть](../ae2-mechanics/me-network-connections.md) на бесконечные
расстояния и даже между измерениями. Они вмещают в общей сложности 32 канала (независимо от того, как
подключены кабели к каждой грани), по сути работая как беспроводной [плотный кабель](cables.md#dense-cable).

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/quantum_bridge_internal_structure_1.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/quantum_bridge_internal_structure_2.snbt" />

  <BoxAnnotation color="#33dd33" min="1 1 1" max="6 2 3">
        Воображаемый кабель между двумя концами
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Важно: **обе стороны должны быть прогружены**, поэтому если две стороны далеко друг от друга, нужно
использовать <ItemLink id="spatial_anchor" /> или другой загрузчик чанков.

# Квантовое кольцо

<BlockImage id="quantum_ring" scale="8" />

Восемь таких блоков вокруг <ItemLink id="quantum_link" /> создадут квантовый сетевой мост. Сетевые
подключения принимают только 4 <ItemLink id="quantum_ring" />, прилегающих к <ItemLink id="quantum_link" />;
4 угловых блока не могут подключаться к кабелям.

## Рецепт

<RecipeFor id="quantum_ring" />

# Камера квантовой связи

<BlockImage id="quantum_link" scale="8" />

Один такой блок, окружённый <ItemLink id="quantum_ring" />, создаст квантовый сетевой мост. Этот блок
не подключается ни к каким кабелям и регистрируется как часть сети, только когда построен полный мост.

Инвентарь этого блока вмещает лишь одну <ItemLink id="quantum_entangled_singularity" /> и доступен
для автоматизации.

## Рецепт

<RecipeFor id="quantum_link" />

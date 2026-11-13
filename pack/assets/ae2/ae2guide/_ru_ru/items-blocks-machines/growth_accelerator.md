---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Ускоритель роста"
  icon: growth_accelerator
  position: 310
categories:
- machines
item_ids:
- ae2:growth_accelerator
---

# Ускоритель роста

<BlockImage id="growth_accelerator" p:powered="true" scale="8"/>

Ускоритель роста значительно ускоряет [рост](../ae2-mechanics/certus-growth.md) истинного кварца или аметиста, если поставить его рядом с цветущим блоком.

Любопытно, что он *также* ускоряет рост различных растений.

Он делает это, применяя «случайные тики» к соседним блокам в дополнение к тем, что случаются естественным образом.
В теории это означает, что 1 ускоритель ускоряет рост примерно в 90 раз по сравнению с обычным, а эффекты нескольких ускорителей складываются.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/growth_accelerator.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Энергию можно подавать сверху или снизу — либо по [кабелям](cables.md) AE2, либо по кабелям энергии из других модов. Ускоритель
принимает как энергию AE2 (AE), так и Forge Energy (FE).

Чтобы запитать его вручную, поставьте <ItemLink id="crank" /> сверху или снизу и щёлкайте по ней правой кнопкой мыши.

Верх и низ можно опознать по розовым флюисовым деталям на них.

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/accelerator_connections.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Рецепт

<RecipeFor id="growth_accelerator" />

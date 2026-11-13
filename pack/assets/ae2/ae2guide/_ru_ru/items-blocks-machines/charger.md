---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Зарядник"
  icon: charger
  position: 310
categories:
- machines
item_ids:
- ae2:charger
---

# Зарядник

<BlockImage id="charger" scale="8" />

Зарядник позволяет заряжать поддерживаемые инструменты и <ItemLink id="certus_quartz_crystal" />.

Энергия подаётся сверху или снизу — либо по [кабелям](cables.md) AE2, либо по кабелям энергии из других модов.
Он принимает как энергию AE2 (AE), так и Forge Energy (FE). Предметы можно вставлять и извлекать с любой стороны.
Извлечь можно только результаты, так что не нужны фильтры, чтобы случайно вынуть кристалл истинного кварца
вместо заряженного. Зарядник можно вращать <ItemLink id="certus_quartz_wrench" />, чтобы удобнее было автоматизировать.

В нём можно получать <ItemLink id="charged_certus_quartz_crystal" />
из <ItemLink id="certus_quartz_crystal" />, а также <ItemLink id="meteorite_compass" /> из <ItemLink id="minecraft:compass" />.

Чтобы запитать его вручную, поставьте <ItemLink id="crank" /> сверху или снизу и щёлкайте по ней правой кнопкой мыши,
пока предмет не зарядится.

Он также служит рабочей станцией для [Исследователя флюкса](fluix_researcher.md).

## Простая автоматизация

Например, возможность вращения позволяет полуавтоматизировать зарядники вот так:

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/charger_hopper.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Рецепт

<RecipeFor id="charger" />

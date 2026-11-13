---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Энергохранилища"
  icon: energy_cell
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:energy_cell
- ae2:dense_energy_cell
- ae2:creative_energy_cell
---

# Энергохранилища

<Row gap="20">
  <BlockImage id="energy_cell" scale="8" p:fullness="4" />

  <BlockImage id="dense_energy_cell" scale="8" p:fullness="4" />

  <BlockImage id="creative_energy_cell" scale="8" />
</Row>

Энергохранилища увеличивают запас [энергии](../ae2-mechanics/energy.md) сети. Небольшой запас энергии помогает сгладить
скачки потребления, когда за раз вставляется или извлекается много предметов, а большая ёмкость
позволяет сети работать, когда энергия не вырабатывается (например ночью при питании от солнечных панелей), или справляться с огромным мгновенным
расходом энергии у [пространственного хранилища](../ae2-mechanics/spatial-io.md).

## Индикаторы заполнения

<Row>
<BlockImage id="energy_cell" scale="4" p:fullness="0" />
<BlockImage id="energy_cell" scale="4" p:fullness="1" />
<BlockImage id="energy_cell" scale="4" p:fullness="2" />
<BlockImage id="energy_cell" scale="4" p:fullness="3" />
<BlockImage id="energy_cell" scale="4" p:fullness="4" />
</Row>

Полосы на боковой грани энергохранилища соответствуют уровню его заряда.

*   0 — заряд ниже 25 %
*   1 — заряд от 25 % до 50 %
*   2 — заряд от 50 % до 75 %
*   3 — заряд от 75 % до 99 %
*   4 — заряд выше 99 %

## Виды ячеек

*   «<ItemLink id="energy_cell" />» вмещает 200 тыс. AE, и одного хватит для большинства случаев: оно с лёгкостью справляется скачками
    потребления при обычной работе сети.
*   «<ItemLink id="dense_energy_cell" />» вмещает 1,6 млн AE и пригодится, если вы хотите питать сеть от накопленной энергии или
    справляться с огромным мгновенным расходом энергии у крупных установок [пространственного хранилища](../ae2-mechanics/spatial-io.md).
*   «<ItemLink id="creative_energy_cell" />» — предмет творческого режима для испытаний, выдающий БЕСКОНЕЧНУЮ МОООЩЬ или как там её.

## Рецепты

<Row>
  <RecipeFor id="energy_cell" />

  <RecipeFor id="dense_energy_cell" />
</Row>

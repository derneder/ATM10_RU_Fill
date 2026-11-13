---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Цветущий истинный кварц"
  icon: flawless_budding_quartz
  position: 010
categories:
- misc ingredients blocks
item_ids:
- ae2:flawless_budding_quartz
- ae2:flawed_budding_quartz
- ae2:chipped_budding_quartz
- ae2:damaged_budding_quartz
- ae2:small_quartz_bud
- ae2:medium_quartz_bud
- ae2:large_quartz_bud
- ae2:quartz_cluster
---

# Цветущий истинный кварц

(см. также [Рост истинного кварца](../ae2-mechanics/certus-growth.md))

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/budding_blocks.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Почки истинного кварца прорастают на цветущих блоках истинного кварца, похоже на аметист. Такие блоки можно найти
в [метеоритах](../ae2-mechanics/meteorites.md). Существует 4 уровня цветущих блоков истинного кварца: безупречный,
несовершенный, потресканный и повреждённый. Проще всего отличить их с помощью модов вроде HWYLA, Jade,
The One Probe и т. п. (или экрана отладки по F3).

У несовершенного, потресканного и повреждённого цветущего истинного кварца при каждом переходе почки на следующую
стадию роста есть шанс, что блок деградирует на один уровень, пока в итоге не превратится в обычный
<ItemLink id="quartz_block" />.

Безупречный цветущий истинный кварц не деградирует от роста почек и работает как бесконечный источник.

Если разрушить цветущие блоки обычной киркой, они деградируют на 1 уровень. Если разрушить киркой
с зачарованием «Шёлковое касание», они не деградируют, за исключением безупречного. **Это значит, что безупречные
цветущие блоки истинного кварца невозможно подобрать и переместить киркой**. Вместо этого для вырезания
и вставки безупречных цветущих блоков можно использовать [пространственное хранилище](../ae2-mechanics/spatial-io.md).

## Рецепты

Несовершенный, потресканный и повреждённый цветущий истинный кварц можно скрафтить, бросив в воду блок
предыдущего уровня (или <ItemLink id="quartz_block" />) вместе с одним или несколькими
<ItemLink id="charged_certus_quartz_crystal" />.

Безупречный цветущий истинный кварц скрафтить нельзя, его можно только найти в мире.

<Row>
  <RecipeFor id="damaged_budding_quartz" />

  <RecipeFor id="chipped_budding_quartz" />

  <RecipeFor id="flawed_budding_quartz" />
</Row>

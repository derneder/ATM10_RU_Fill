---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: "Рост истинного кварца"
  icon: quartz_cluster
---

# Рост истинного кварца

## По сути, просто скопировано со страницы «Начало работы»

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/budding_certus_1.snbt" />
</GameScene>

Бутоны истинного кварца вырастают на [цветущих блоках истинного кварца](../items-blocks-machines/budding_certus.md), подобно аметисту. Если сломать бутон, который ещё не закончил
расти, из него выпадет 1 шт. предмета «<ItemLink id="certus_quartz_dust" />», и удача на это не влияет. Если сломать полностью выросший кластер, выпадет 4 шт. предмета
«<ItemLink id="certus_quartz_crystal" />», и зачарование «Удача» увеличит это число.

Существует 4 уровня цветущих блоков истинного кварца: безупречный, несовершенный, потресканный и повреждённый, и изначально
их можно найти в [метеоритах](../ae2-mechanics/meteorites.md).

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/budding_blocks.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Каждый раз, когда бутон вырастает на одну стадию, цветущий блок с некоторым шансом деградирует на один уровень, в конце концов превратившись
в обычный блок истинного кварца. Их можно восстановить (и создать новые цветущие блоки), бросив цветущий блок (или
блок истинного кварца) в воду вместе с одним или несколькими предметами «<ItemLink id="charged_certus_quartz_crystal" />».

<RecipeFor id="damaged_budding_quartz" />

Безупречные цветущие блоки истинного кварца не деградируют и будут бесконечно производить истинный кварц. Однако их нельзя изготовить или переместить
киркой, даже с шёлковым касанием. (Хотя их *можно* переместить с помощью [пространственного хранилища](../ae2-mechanics/spatial-io.md).)

Сами по себе бутоны истинного кварца растут очень медленно. К счастью, <ItemLink id="growth_accelerator" /> значительно
ускоряет этот процесс, если поставить его рядом с цветущим блоком. Постройте несколько таких в первую очередь.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/budding_certus_2.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Из-за сложных взаимодействий каждая закрытая сторона цветущего блока замедляет суммарную скорость роста от этого блока,
и в итоге этот эффект перевешивает действие дополнительных ускорителей. Эмпирические проверки показывают следующее:

![Items/min for ratios](../assets/diagrams/certus_farm_speed_chart_1.png)

![common setups](../assets/diagrams/certus_farm_speed_chart_2.png)

Если вам не хватает кварца, чтобы сделать ещё и «<ItemLink id="energy_acceptor" />» или «<ItemLink id="vibration_chamber" />»,
можно сделать «<ItemLink id="crank" />» и приставить её к концу ускорителя.

Автоматический сбор истинного кварца [описан здесь](../example-setups/simple-certus-farm.md).
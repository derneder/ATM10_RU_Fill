---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "МЭ плоскость уничтожения"
  icon: annihilation_plane
  position: 210
categories:
- devices
item_ids:
- ae2:annihilation_plane
---

# МЭ плоскость уничтожения

<GameScene zoom="8" background="transparent">
<ImportStructure src="../assets/blocks/annihilation_plane.snbt" />
</GameScene>

МЭ плоскость уничтожения разрушает блоки и подбирает предметы. Она работает похоже на <ItemLink id="import_bus" />,
отправляя всё в [сетевое хранилище](../ae2-mechanics/import-export-storage.md). Чтобы предмет был подобран, он должен
столкнуться с гранью плоскости — плоскость не подбирает предметы по площади.

Плоскости уничтожения можно зачаровать любым зачарованием для кирок, так что да, можно наложить безумные уровни
«Удачи» на пару штук и [автоматизировать обработку руды](../example-setups/ore-fortuner.md), если ваш модпак это позволяет.
Кроме того, «Шёлковое касание» делает то, что от него и ждёшь, «Эффективность» снижает энергозатраты на разрушение
блока, а «Прочность» даёт шанс вообще не потратить энергию.

Они являются [частями кабеля](../ae2-mechanics/cable-subparts.md).

**НЕ ЗАБУДЬТЕ ВКЛЮЧИТЬ FAKE PLAYERS В ПРИВАТЕ ЧАНКА**

## Фильтрация

Плоскость уничтожения разрушает блок или подбирает предмет, только если может хранить полученные дропы/предметы
в своей сети. Это значит, что для фильтрации *нужно ограничить, что может храниться в её сети*, проще всего
поместив её в [подсеть](../ae2-mechanics/subnetworks.md). Для этого можно <ItemLink id="storage_bus" /> или
[ячейку](../items-blocks-machines/storage_cells.md) [разметить](cell_workbench.md).

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/annihilation_filtering.snbt" />

  <DiamondAnnotation pos="1 0.5 0.5" color="#00ff00">
        Отфильтровано по тому, что дропается с того, что вы хотите разрушать.
  </DiamondAnnotation>

  <DiamondAnnotation pos=".5 0.5 2.5" color="#00ff00">
        Разметка по тому, что дропается с того, что вы хотите разрушать.
  </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Ещё раз: фильтрация идёт *по дропам*, так что, например, если вы хотите фильтровать разрушение <ItemLink id="minecraft:amethyst_cluster" />,
нужна плоскость с зачарованием «Шёлковое касание», иначе каждая предыдущая стадия роста не дропает ничего,
и плоскость будет разрушать их независимо от фильтра, ведь сеть всегда может хранить «ничто».

## Рецепт

<RecipeFor id="annihilation_plane" />

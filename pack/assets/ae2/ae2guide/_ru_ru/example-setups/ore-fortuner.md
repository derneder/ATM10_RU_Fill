---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Автоматический фортунатор руды"
  icon: minecraft:raw_iron
---

# Автоматизация фортунирования руды

<ItemLink id="annihilation_plane" /> можно зачаровать любым зачарованием для кирки, включая Удачу, поэтому очевидный способ применения —
наложить Удачу на несколько таких плоскостей, а затем с помощью плоскостей «<ItemLink id="formation_plane" />» и «<ItemLink id="annihilation_plane" />» быстро
ставить и ломать руду.

Учтите: шины «<ItemLink id="import_bus" />» «разгоняются», поэтому схема сначала работает медленно, а через несколько секунд выходит на полную скорость.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/ore_fortuner.snbt" />

  <BoxAnnotation color="#dddddd" min="2.7 0 2" max="3 1 3">
        (1) Шина импорта: внутри несколько карт ускорения.
        <ItemImage id="speed_card" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 0 2" max="2 1 2.3">
        (2) Плоскости формирования: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 0 0.7" max="2 1 1">
        (3) Плоскости уничтожения: окна настройки нет, но зачарованы на Удачу.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2.7 0 0" max="3 1 1">
        (4) Шина хранения: в конфигурации по умолчанию.
  </BoxAnnotation>

<DiamondAnnotation pos="3.5 0.5 2.5" color="#00ff00">
        Вход
    </DiamondAnnotation>

<DiamondAnnotation pos="3.5 0.5 0.5" color="#00ff00">
        Выход
    </DiamondAnnotation>

<DiamondAnnotation pos="4 0.5 1.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

*   <ItemLink id="import_bus" /> (1) содержит несколько карт «<ItemLink id="speed_card" />». Чем больше плоскостей формирования
    в массиве, тем больше таких карт нужно: они заставляют шину импорта вытягивать больше предметов за раз.
*   Плоскости «<ItemLink id="formation_plane" />» (2) находятся в конфигурации по умолчанию.
*   Плоскости «<ItemLink id="annihilation_plane" />» (3) не имеют окна настройки и не настраиваются, но зачарованы на Удачу.
*   <ItemLink id="storage_bus" /> (4) находится в конфигурации по умолчанию.

## Как это работает

1.  <ItemLink id="import_bus" /> в зелёной подсети импортирует блоки из первой бочки в [сетевое хранилище](../ae2-mechanics/import-export-storage.md)
2.  Единственное хранилище в зелёной подсети — <ItemLink id="formation_plane" />, которая ставит блоки.
3.  <ItemLink id="annihilation_plane" /> в оранжевой подсети ломает блоки, применяя к ним Удачу.
4.  <ItemLink id="storage_bus" /> в оранжевой подсети складывает результаты ломания во вторую бочку.

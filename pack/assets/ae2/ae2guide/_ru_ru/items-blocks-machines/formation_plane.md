---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "МЭ плоскость формирования"
  icon: formation_plane
  position: 210
categories:
- devices
item_ids:
- ae2:formation_plane
---

# МЭ плоскость формирования

<GameScene zoom="8" background="transparent">
  <ImportStructure src="../assets/blocks/formation_plane.snbt" />
</GameScene>

МЭ плоскость формирования ставит блоки и выбрасывает предметы. Она работает как <ItemLink id="storage_bus" />, в который разрешено только вставлять: она ставит блоки и выбрасывает предметы, когда [устройства](../ae2-mechanics/devices.md) «сохраняют» в неё вещи, вставляя их в [сетевое хранилище](../ae2-mechanics/import-export-storage.md), — например, <ItemLink id="import_bus" /> и <ItemLink id="interface" />.

<GameScene zoom="8" interactive={true}>
  <ImportStructure src="../assets/assemblies/formation_plane_demonstration.snbt" />
  <IsometricCamera yaw="255" pitch="30" />
</GameScene>

Обратите внимание: это то же самое, что и связки «шина импорта → шина хранения» и «интерфейс → шина хранения» в [кабельных подсетях](../example-setups/pipe-subnet.md).

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/import_storage_pipe.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/interface_storage_pipe.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Это [устройство](../ae2-mechanics/devices.md) использует те же механики, что и шины хранения в [кабельных подсетях](../example-setups/pipe-subnet.md), и может заменить шины хранения в таких схемах, если вместо перемещения предметов нужно выбрасывать предметы или ставить блоки.

Это [кабельные подчасти](../ae2-mechanics/cable-subparts.md).

**НЕ ЗАБУДЬТЕ РАЗРЕШИТЬ ДОСТУП ФЕЙКОВЫМ ИГРОКАМ В ВАШЕМ ПРИВАТЕ ЧАНКОВ**

## Фильтрация

По умолчанию плоскость ставит и выбрасывает что угодно. Предметы, помещённые в её слоты фильтра, работают как белый список: ставиться будут только эти конкретные предметы.

Предметы и жидкости можно перетаскивать в слоты из JEI/REI, даже если у вас их на самом деле нет.

Щелчок правой кнопкой мыши с жидкостной ёмкостью в руке (например, ведром или резервуаром) задаёт фильтр по этой жидкости, а не по предмету ёмкости.

## Приоритет

Приоритет задаётся нажатием на гаечный ключ в правом верхнем углу окна.
Предметы, попадающие в сеть, в первую очередь направляются в хранилище с наивысшим приоритетом.

## Настройки

*   Плоскость можно настроить на постановку блоков в мире или на выбрасывание предметов

## Улучшения

МЭ плоскость формирования поддерживает следующие [улучшения](upgrade_cards.md):

*   <ItemLink id="capacity_card" /> увеличивает количество слотов фильтра
*   <ItemLink id="fuzzy_card" /> позволяет фильтровать по уровню прочности и/или игнорировать NBT предмета
*   <ItemLink id="inverter_card" /> превращает фильтр из белого списка в чёрный

## Рецепт

<RecipeFor id="formation_plane" />

---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "МЭ порт ввода/вывода"
  icon: io_port
  position: 210
categories:
- devices
item_ids:
- ae2:io_port
---

# МЭ порт ввода/вывода

<BlockImage id="io_port" p:powered="true" scale="8" />

МЭ порт ввода/вывода позволяет быстро заполнять [ячейки хранения](../items-blocks-machines/storage_cells.md) из [сетевого хранилища](../ae2-mechanics/import-export-storage.md) и обратно, а также опустошать их.

Его можно поворачивать <ItemLink id="certus_quartz_wrench" />.

## Настройки

*   МЭ порт ввода/вывода можно настроить на перемещение ячейки в выходные слоты, когда ячейка пуста, заполнена или когда работа завершена.
*   Если вставить <ItemLink id="redstone_card" />, появятся опции для различных редстоун-условий
*   В центре окна находится стрелка, задающая направление передачи предметов: из ячейки в [сетевое хранилище](../ae2-mechanics/import-export-storage.md) или из хранилища в ячейку.

## Улучшения

МЭ порт ввода/вывода поддерживает следующие [улучшения](upgrade_cards.md):

*   <ItemLink id="speed_card" /> увеличивает количество перемещаемых вещей за операцию
*   <ItemLink id="redstone_card" /> добавляет редстоун-управление: работа при сильном сигнале, при слабом сигнале или один раз за импульс

## Рецепт

<RecipeFor id="io_port" />

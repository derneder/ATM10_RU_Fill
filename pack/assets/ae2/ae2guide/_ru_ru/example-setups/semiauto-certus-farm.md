---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Полуавтоматическая ферма истинного кварца"
  icon: certus_quartz_crystal
  position: 115
---

# Полуавтоматическая ферма истинного кварца

К сожалению, чтобы [простая ферма истинного кварца](simple-certus-farm.md) работала полностью
автоматически, ей нужен «<ItemLink id="flawless_budding_quartz" />». Для этого требуется либо [пространственный ввод/вывод](../ae2-mechanics/spatial-io.md), либо постройка фермы у [метеорита](../ae2-mechanics/meteorites.md).

Однако AE2 умеет ставить и ломать блоки, так что, возможно,
ферма сможет *сама заменять цветущий блок истинного кварца*. (Вам придётся периодически
класть «<ItemLink id="flawed_budding_quartz" />» во входную бочку и доставать «<ItemLink id="quartz_block" />» из
бочки с отработанными цветущими блоками)

Чтобы сделать это полностью автоматически, обратитесь к странице [Продвинутая ферма истинного кварца](advanced-certus-farm.md).

Эта ферма немного сложнее [простой фермы истинного кварца](simple-certus-farm.md), потому что на самом деле это
3 отдельные установки, втиснутые в одну.

Примерные скорости смотрите в статье [Рост истинного кварца](../ae2-mechanics/certus-growth.md).

**ЭТО СЛОЖНАЯ ПОСТРОЙКА, В КОТОРОЙ ОДНО СПРЯТАНО ЗА ДРУГИМ, ВРАЩАЙТЕ КАМЕРУ, ЧТОБЫ УВИДЕТЬ ЕЁ СО ВСЕХ СТОРОН**

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/semiauto_certus_farm.snbt" />

  <BoxAnnotation color="#ddaaaa" min="3.7 2 1" max="4 3 2">
        (1) Плоскость уничтожения № 1: окна настройки нет, но её можно зачаровать на Удачу.
  </BoxAnnotation>

  <BoxAnnotation color="#ddaaaa" min="2 2 1" max="2.3 3 2">
        (2) Шина хранения №1: фильтр на кристалл истинного кварца.
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 2.5 1.5" color="#ff0000">
    Подсеть разрушителя кластеров
  </DiamondAnnotation>

  <BoxAnnotation color="#aaddaa" min="3.7 1 1" max="4 2 2">
        (3) Плоскость уничтожения № 2: окна настройки нет, но она зачарована на Шёлковое касание.
  </BoxAnnotation>

  <BoxAnnotation color="#aaddaa" min="2 1 1" max="2.3 2 2">
        (4) Шина хранения №2: фильтр на блок истинного кварца.
        <BlockImage id="quartz_block" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 1.5 1.5" color="#00ff00">
    Подсеть разрушителя блоков истинного кварца
  </DiamondAnnotation>

  <BoxAnnotation color="#ffddaa" min="4 0.7 1" max="5 1 2">
        (5) Плоскость формирования: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#ffddaa" min="2 0 1" max="2.3 1 2">
        (6) Шина импорта: в конфигурации по умолчанию.
  </BoxAnnotation>

  <DiamondAnnotation pos="3 0.5 1.5" color="#ddcc00">
    Подсеть установщика цветущих блоков
  </DiamondAnnotation>

  <BoxAnnotation color="#aaaadd" min="0.7 2 1" max="1 3 2">
        (7) Шина хранения №3: фильтр на кристалл истинного кварца. Приоритет выше, чем у вашего основного хранилища.
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

    <DiamondAnnotation pos="1.5 0.5 1.5" color="#00ff00">
        Вручную вставляйте несовершенный цветущий блок истинного кварца.
        <BlockImage id="flawed_budding_quartz" scale="2" />
    </DiamondAnnotation>

    <DiamondAnnotation pos="1.5 1.5 1.5" color="#00ff00">
        Вручную извлекайте блок истинного кварца.
        <BlockImage id="quartz_block" scale="2" />
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0" color="#00ff00">
        В основную МЭ-сеть
    </DiamondAnnotation>

  <IsometricCamera yaw="165" pitch="5" />
</GameScene>

## Конфигурации

### Разрушитель кластеров:

* <ItemLink id="annihilation_plane" /> (1) — первая по счёту: окна настройки у неё нет, но её можно зачаровать на Удачу.
* <ItemLink id="storage_bus" /> (2) — первая по счёту: фильтр настроен на предмет «<ItemLink id="certus_quartz_crystal" />».

### Разрушитель блоков истинного кварца:

* <ItemLink id="annihilation_plane" /> (3) — вторая по счёту: окна настройки у неё нет, но её необходимо зачаровать на Шёлковое касание.
* <ItemLink id="storage_bus" /> (4) — вторая по счёту: фильтр настроен на предмет «<ItemLink id="quartz_block" />».

### Установщик цветущих блоков:

* <ItemLink id="formation_plane" /> (5) находится в конфигурации по умолчанию.
* <ItemLink id="import_bus" /> (6) находится в конфигурации по умолчанию.

### В основной сети:

* Третья шина хранения «<ItemLink id="storage_bus" />» (7) настроена на «<ItemLink id="certus_quartz_crystal" />», и её
  [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority) выше, чем у вашего основного хранилища.

## Как это работает

### Разрушитель кластеров:

Подсеть разрушителя кластеров работает почти так же, как подсеть в [простой ферме истинного кварца](simple-certus-farm.md).

1. <ItemLink id="annihilation_plane" /> пытается сломать то, что находится перед ней, но может сломать только блок «<ItemLink id="quartz_cluster" />»,
   потому что единственное хранилище в подсети — <ItemLink id="storage_bus" /> с фильтром на предмет «<ItemLink id="certus_quartz_crystal" />».
2. <ItemLink id="storage_bus" /> складывает кристаллы истинного кварца в бочку.

### Разрушитель блоков истинного кварца

Подсеть разрушителя блоков истинного кварца ломает истощённый цветущий блок, когда тот превращается в обычный блок «<ItemLink id="quartz_block" />».
Работает она так же, как разрушитель кластеров.

1. <ItemLink id="annihilation_plane" /> пытается сломать то, что находится перед ней, но может сломать только «<ItemLink id="quartz_block" />»,
   потому что единственное хранилище в подсети — это «<ItemLink id="storage_bus" />» с фильтром на «<ItemLink id="quartz_block" />».
   Плоскость должна быть зачарована «Шёлковым касанием», чтобы цветущий блок не ухудшался при разрушении и плоскость не сломала его раньше времени.
2. <ItemLink id="storage_bus" /> помещает блок истинного кварца в бочку
   с отработанными цветущими блоками; чтобы обновить его, вам придётся вручную бросить его в воду вместе с «<ItemLink id="charged_certus_quartz_crystal" />».

### Установщик цветущих блоков

Подсеть установщика цветущих блоков ставит новый блок «<ItemLink id="flawed_budding_quartz" />», когда подсеть-разрушитель ломает старый истощённый.

1. <ItemLink id="import_bus" /> импортирует цветущий блок из входной бочки.
2. Единственное хранилище в подсети — это <ItemLink id="formation_plane" />, которая ставит цветущий блок.

### В основной сети

* <ItemLink id="storage_bus" /> даёт основной сети (а также [автоматизации зарядника](charger-automation.md)) доступ ко всем кристаллам истинного кварца в бочке. У неё
  высокий [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чтобы кристаллы истинного кварца в первую очередь
  возвращались в бочку, а не в ваше основное хранилище.
---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Продвинутая ферма истинного кварца"
  icon: certus_quartz_crystal
  position: 120
---

# Продвинутая ферма истинного кварца

По сути, это [полуавтоматическая ферма истинного кварца](semiauto-certus-farm.md), только полностью встроенная
в вашу МЭ-систему.

Вместо большого запаса цветущих блоков, которые время от времени приходится обновлять вручную,
эта установка использует [автоматизацию зарядника](charger-automation.md) и [автоматизацию с бросанием в воду](throw-in-water-automation.md),
чтобы делать это автоматически.

Примерные скорости смотрите в статье [Рост истинного кварца](../ae2-mechanics/certus-growth.md).

**ЭТО СЛОЖНАЯ ПОСТРОЙКА, В КОТОРОЙ ОДНО СПРЯТАНО ЗА ДРУГИМ, ВРАЩАЙТЕ КАМЕРУ, ЧТОБЫ УВИДЕТЬ ЕЁ СО ВСЕХ СТОРОН**

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/advanced_certus_farm.snbt" />

  <BoxAnnotation color="#ddaaaa" min="3.7 2 1" max="4 3 2">
        (1) Плоскость уничтожения № 1: окна настройки нет, но её можно зачаровать на Удачу.
  </BoxAnnotation>

  <BoxAnnotation color="#ddaaaa" min="2 2 1.7" max="3 3 2">
        (2) Шина хранения № 1: фильтр — кристалл истинного кварца.
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 2.5 1.5" color="#ff0000">
    Подсеть разрушителя кластеров
  </DiamondAnnotation>

  <BoxAnnotation color="#aaddaa" min="3.7 1 1" max="4 2 2">
        (3) Плоскость уничтожения № 2: окна настройки нет, но она зачарована на Шёлковое касание.
  </BoxAnnotation>

  <BoxAnnotation color="#aaddaa" min="2 1 1.7" max="3 2 2">
        (4) Шина хранения № 2: фильтр — блок истинного кварца.
        <BlockImage id="quartz_block" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 1.5 1.5" color="#00ff00">
    Подсеть разрушителя блоков истинного кварца
  </DiamondAnnotation>

  <BoxAnnotation color="#ffddaa" min="4 0.7 1" max="5 1 2">
        (5) Плоскость формирования: в конфигурации по умолчанию.
  </BoxAnnotation>

  <BoxAnnotation color="#ffddaa" min="2 0.7 2" max="3 1 3">
        (6) Шина импорта: фильтр — несовершенный цветущий блок истинного кварца.
        <BlockImage id="flawed_budding_quartz" scale="2" />
  </BoxAnnotation>

  <DiamondAnnotation pos="3 0.5 1.5" color="#ddcc00">
    Подсеть установщика цветущих блоков
  </DiamondAnnotation>

  <BoxAnnotation color="#aaaadd" min="1.7 2 2" max="2 3 3">
        (7) Шина хранения № 3: фильтр — кристалл истинного кварца. Приоритет выше, чем у основного хранилища.
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#aaaadd" min="2 1 2" max="3 2 3">
        (8) Интерфейс: настроен хранить у себя 1 несовершенный цветущий блок истинного кварца, в нём стоит карта изготовления.
        <Row><BlockImage id="flawed_budding_quartz" scale="2" /> <ItemImage id="crafting_card" scale="2" /></Row>
  </BoxAnnotation>

<DiamondAnnotation pos="1.5 0.5 0" color="#00ff00">
        К основной сети, автоматизации зарядника и автоматизации с бросанием в воду
        <Row>
        <GameScene zoom="3" background="transparent">
          <ImportStructure src="../assets/assemblies/charger_automation.snbt" />
          <IsometricCamera yaw="195" pitch="30" />
        </GameScene>
        <GameScene zoom="3" background="transparent">
          <ImportStructure src="../assets/assemblies/throw_in_water.snbt" />
          <IsometricCamera yaw="195" pitch="30" />
        </GameScene>
        </Row>
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

* <ItemLink id="formation_plane" /> (5) оставлена в конфигурации по умолчанию.
* <ItemLink id="import_bus" /> (6) настроена на фильтр по предмету «<ItemLink id="flawed_budding_quartz" />».

### В основной сети:

* <ItemLink id="storage_bus" /> (7) — третья по счёту: фильтр настроен на предмет «<ItemLink id="certus_quartz_crystal" />», а
  [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority) выше, чем у основного хранилища.
* <ItemLink id="interface" /> (8) настроен хранить у себя 1 несовершенный цветущий блок истинного кварца, и в нём стоит «<ItemLink id="crafting_card" />».

## Как это работает

### Разрушитель кластеров:

Подсеть разрушителя кластеров работает почти так же, как подсеть в [простой ферме истинного кварца](simple-certus-farm.md).

1. <ItemLink id="annihilation_plane" /> пытается сломать то, что находится перед ней, но может сломать только блок «<ItemLink id="quartz_cluster" />»,
   потому что единственное хранилище в подсети — <ItemLink id="storage_bus" /> с фильтром на предмет «<ItemLink id="certus_quartz_crystal" />».
2. <ItemLink id="storage_bus" /> складывает кристаллы истинного кварца в бочку.

### Разрушитель блоков истинного кварца

Подсеть разрушителя блоков истинного кварца ломает истощённый цветущий блок, когда тот превращается в обычный блок «<ItemLink id="quartz_block" />».
Работает она так же, как разрушитель кластеров.

1. <ItemLink id="annihilation_plane" /> пытается сломать то, что находится перед ней, но может сломать только блок «<ItemLink id="quartz_block" />»,
   потому что единственное хранилище в подсети — <ItemLink id="storage_bus" /> с фильтром на блок «<ItemLink id="quartz_block" />». 
   У плоскости должно быть шёлковое касание: так цветущий блок не деградирует при ломании, а значит, плоскость не сломает его раньше времени.
2. <ItemLink id="storage_bus" /> складывает блок истинного кварца в блок «<ItemLink id="interface" />», чтобы
   [автоматизация с бросанием в воду](throw-in-water-automation.md) могла использовать его для создания нового блока «<ItemLink id="flawed_budding_quartz" />».

### Установщик цветущих блоков

Подсеть установщика цветущих блоков ставит новый блок «<ItemLink id="flawed_budding_quartz" />», когда подсеть-разрушитель ломает старый истощённый.

1. <ItemLink id="import_bus" /> импортирует цветущий блок из блока «<ItemLink id="interface" />» в [сетевое хранилище](../ae2-mechanics/import-export-storage.md)
2. Единственное хранилище в подсети — <ItemLink id="formation_plane" />, которая ставит цветущий блок.

### В основной сети

* <ItemLink id="storage_bus" /> даёт основной сети (а также [автоматизации зарядника](charger-automation.md)) доступ ко всем кристаллам истинного кварца в бочке. Она настроена на
  высокий [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чтобы кристаллы истинного кварца в первую очередь
  возвращались в бочку, а не в ваше основное хранилище.
* <ItemLink id="interface" /> даёт подсети установщика цветущих блоков доступ к блоку «<ItemLink id="flawed_budding_quartz" />», а
    подсети разрушителя блоков истинного кварца — способ вернуть истощённые блоки в основную сеть.
    <ItemLink id="crafting_card" /> позволяет интерфейсу запрашивать новые цветущие блоки у [автокрафта](../ae2-mechanics/autocrafting.md) основной сети.
---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Простая ферма истинного кварца"
  icon: certus_quartz_crystal
  position: 110
---

# Простая ферма истинного кварца

Как сказано на странице [Рост истинного кварца](../ae2-mechanics/certus-growth.md), для автоматизации сбора «<ItemLink id="certus_quartz_crystal" />»
используются плоскости «<ItemLink id="annihilation_plane" />» и шины «<ItemLink id="storage_bus" />». 
Ускорители «<ItemLink id="growth_accelerator" />» многократно ускоряют рост бутонов истинного кварца, а затем плоскости
ломают полностью выросшие кластеры «<ItemLink id="quartz_cluster" />». Фильтрация достигается за счёт подозрительно удачной особенности: незрелые
бутоны истинного кварца выбрасывают «<ItemLink id="certus_quartz_dust" />» вместо того, чтобы не выбрасывать ничего.

Эта ферма работает полностью автоматически с блоком «<ItemLink id="flawless_budding_quartz" />», но с несовершенным, потресканным и повреждённым
цветущим блоком истинного кварца цветущий блок придётся менять вручную. Или автоматически, как описано на страницах [Полуавтоматическая ферма истинного кварца](semiauto-certus-farm.md)
и [Продвинутая ферма истинного кварца](advanced-certus-farm.md).

Примерные скорости смотрите в статье [Рост истинного кварца](../ae2-mechanics/certus-growth.md).

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/simple_certus_farm.snbt" />

  <BoxAnnotation color="#dddddd" min="3.7 1 1" max="4 2 2">
        (1) Плоскость уничтожения: окна настройки нет, но её можно зачаровать «Удачей».
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 1" max="3.3 2 2">
        (2) Шина хранения №1: фильтр на кристалл истинного кварца.
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="3 1 .7" max="2 2 1">
        (3) Шина хранения №2: фильтр на кристалл истинного кварца. Приоритет выше, чем у основного хранилища.
        <ItemImage id="certus_quartz_crystal" scale="2" />
  </BoxAnnotation>

<DiamondAnnotation pos="1 0.5 0.5" color="#00ff00">
        В основную МЭ-сеть
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

* Первая плоскость «<ItemLink id="annihilation_plane" />» (1) не имеет окна настройки, но её можно зачаровать «Удачей».
* Первая шина хранения «<ItemLink id="storage_bus" />» (2) настроена на «<ItemLink id="certus_quartz_crystal" />».
* Вторая шина хранения «<ItemLink id="storage_bus" />» (3) настроена на «<ItemLink id="certus_quartz_crystal" />», и её
  [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority) выше, чем у основного хранилища.

## Как это работает

1. <ItemLink id="annihilation_plane" /> пытается сломать то, что находится перед ней, но может сломать только «<ItemLink id="quartz_cluster" />»,
   потому что единственное хранилище в подсети — это «<ItemLink id="storage_bus" />» с фильтром на «<ItemLink id="certus_quartz_crystal" />».
4. Первая шина хранения «<ItemLink id="storage_bus" />» складывает кристаллы истинного кварца в бочку.
5. Вторая шина хранения «<ItemLink id="storage_bus" />» даёт основной сети доступ ко всем кристаллам истинного кварца в бочке. У неё
   высокий [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чтобы кристаллы истинного кварца в первую очередь
   возвращались в бочку, а не в ваше основное хранилище.

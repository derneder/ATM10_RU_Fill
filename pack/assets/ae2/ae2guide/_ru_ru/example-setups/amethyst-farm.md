---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Ферма аметиста"
  icon: minecraft:amethyst_shard
---

# Выращивание аметиста

Хотя <ItemLink id="growth_accelerator" /> действует и на аметист, обычные способы отфильтровать [бутоны истинного кварца](../items-blocks-machines/budding_certus.md)
с помощью предмета «<ItemLink id="annihilation_plane" />» на аметистовые бутоны не работают. В отличие от недозрелых бутонов истинного кварца, из которых выпадает
<ItemLink id="certus_quartz_dust" />, из недозрелых аметистовых бутонов не выпадает ничего, поэтому плоскость уничтожения всегда будет их ломать,
ведь сеть всегда может сохранить «ничего».

Обойти это можно, зачаровав плоскость уничтожения на Шёлковое касание. Тогда недозрелые аметистовые бутоны *будут* что-то выбрасывать
(разные стадии самих блоков-бутонов), а значит, их можно отфильтровать.

Затем блок «<ItemLink id="minecraft:amethyst_cluster" />» нужно снова поставить с помощью предмета «<ItemLink id="formation_plane" />», а потом
заново сломать с помощью предмета «<ItemLink id="annihilation_plane" />» без Шёлкового касания, чтобы получить предметы «<ItemLink id="minecraft:amethyst_shard" />».

Учтите: друза растёт в определённом направлении, поэтому прямо напротив плоскости формирования должна быть грань сплошного блока.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/amethyst_farm.snbt" />

  <BoxAnnotation color="#dddddd" min="2.7 1 1" max="3 2 2">
        (1) Плоскость уничтожения №1: окна настройки нет, но зачарована Шёлковым касанием.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="2 1 1" max="2.3 2 2">
        (2) Плоскость формирования: фильтр — аметистовая друза.
        <ItemImage id="minecraft:amethyst_cluster" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1.3 0.7 1" max="2 1 2">
        (3) Плоскость уничтожения №2: окна настройки нет, но можно зачаровать на Удачу.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="1 0 1" max="1.3 1 2">
        (4) Шина хранения №1: фильтр — осколок аметиста.
        <ItemImage id="minecraft:amethyst_shard" scale="2" />
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="0 0 .7" max="1 1 1">
        (5) Шина хранения №2: фильтр — осколок аметиста. Приоритет выше, чем у основного хранилища.
        <ItemImage id="minecraft:amethyst_shard" scale="2" />
  </BoxAnnotation>

<DiamondAnnotation pos="0 0.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

* Первая <ItemLink id="annihilation_plane" /> (1) не имеет окна настройки и не настраивается, но должна быть зачарована Шёлковым касанием.
* <ItemLink id="formation_plane" /> (2) настроена на фильтрацию по предмету «<ItemLink id="minecraft:amethyst_cluster" />».
* Вторая <ItemLink id="annihilation_plane" /> (3) не имеет окна настройки и не настраивается, но может быть зачарована Удачей.
* Первая <ItemLink id="storage_bus" /> (4) настроена на фильтрацию по предмету «<ItemLink id="minecraft:amethyst_shard" />».
* Вторая <ItemLink id="storage_bus" /> (5) настроена на фильтрацию по предмету «<ItemLink id="minecraft:amethyst_shard" />», и для неё задан более высокий
  [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чем у вашего основного хранилища.

## Как это работает

1. Первая <ItemLink id="annihilation_plane" /> пытается сломать то, что находится перед ней, но может сломать только блок «<ItemLink id="minecraft:amethyst_cluster" />»,
    потому что единственное хранилище в подсети — <ItemLink id="formation_plane" /> с фильтром по аметистовой друзе. Это работает только потому, что
плоскость зачарована Шёлковым касанием, иначе она могла бы ломать неподросшие бутоны, ведь из них ничего не выпадает.
2. <ItemLink id="formation_plane" /> ставит друзу на противоположный от неё блок.
3. Вторая <ItemLink id="annihilation_plane" /> ломает друзу, и в результате получаются предметы «<ItemLink id="minecraft:amethyst_shard" />».
4. Первая <ItemLink id="storage_bus" /> складывает осколки в бочку. Формально фильтр здесь не нужен, ведь единственное,
с чем должна сталкиваться вторая плоскость уничтожения, — полностью выросшие друзы.
5. Вторая <ItemLink id="storage_bus" /> даёт основной МЭ-сети доступ ко всем осколкам аметиста в бочке. Для неё задан высокий
[приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чтобы осколки аметиста возвращались преимущественно в бочку,
а не в ваше основное хранилище.

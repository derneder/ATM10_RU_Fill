---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Подсеть-«труба» для предметов и жидкостей"
  icon: storage_bus
---

# Подсеть-«труба» для предметов и жидкостей

Простой способ имитировать предметную и/или жидкостную трубу с помощью [устройств](../ae2-mechanics/devices.md) AE2, пригодный, ну, для всего, для чего вы использовали бы предметную или жидкостную трубу.
В том числе для возврата результата изготовления в <ItemLink id="pattern_provider" />.

Обычно это можно сделать двумя разными способами:

## Шина импорта -> шина хранения

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/import_storage_pipe.snbt" />

<BoxAnnotation color="#dddddd" min="3.7 0 0" max="4 1 1">
        (1) Шина импорта: можно настроить фильтр.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 1">
        (2) Шина хранения: можно настроить фильтр. Она (и другие шины хранения, которые должны быть пунктами назначения)
        должна быть единственным хранилищем в сети.
  </BoxAnnotation>

<DiamondAnnotation pos="4.5 0.5 0.5" color="#00ff00">
        Источник
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0.5" color="#00ff00">
        Пункт назначения
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<ItemLink id="import_bus" /> (1) на исходном инвентаре импортирует предметы или жидкость и пытается поместить их в [сетевое хранилище](../ae2-mechanics/import-export-storage.md).
Поскольку единственное хранилище в сети — <ItemLink id="storage_bus" /> (2) (именно поэтому это подсеть, а не часть вашей основной МЭ-сети), предметы или жидкость
помещаются в инвентарь назначения и таким образом переносятся. Энергия подаётся через <ItemLink id="quartz_fiber" />.
И для шины импорта, и для шины хранения можно настроить фильтр, но без фильтров схема переносит всё, до чего может дотянуться.
Также схема работает с несколькими шинами импорта и несколькими шинами хранения.

## Шина хранения -> шина экспорта

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/storage_export_pipe.snbt" />

<BoxAnnotation color="#dddddd" min="3.7 0 0" max="4 1 1">
        (1) Шина хранения: можно настроить фильтр. Она (как и другие шины хранения, которые вы хотите сделать источником)
        должна быть единственным хранилищем в сети.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 1">
        (2) Шина экспорта: фильтр обязателен.
  </BoxAnnotation>

<DiamondAnnotation pos="4.5 0.5 0.5" color="#00ff00">
        Источник
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0.5" color="#00ff00">
        Пункт назначения
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<ItemLink id="export_bus" /> на принимающем инвентаре пытается вытянуть предметы из своего фильтра из [сетевого хранилища](../ae2-mechanics/import-export-storage.md).
Поскольку единственное хранилище в сети — это <ItemLink id="storage_bus" /> (поэтому это подсеть, а не часть вашей основной сети), предметы или жидкость
вытягиваются из исходного инвентаря и тем самым переносятся. Энергия подаётся через «<ItemLink id="quartz_fiber" />».
Поскольку шины экспорта работают только с фильтром, эта схема функционирует лишь тогда, когда вы настроите фильтр шины экспорта.
Эта схема работает и с несколькими шинами хранения и несколькими шинами экспорта.

## Схема, которая не работает (шина импорта -> шина экспорта)

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/import_export_pipe.snbt" />

<BoxAnnotation color="#dd3333" min="3.7 0 0" max="4 1 1">
        Шина импорта: в сети нет хранилища, поэтому импортировать некуда.
  </BoxAnnotation>

<BoxAnnotation color="#dd3333" min="1 0 0" max="1.3 1 1">
        (2) Шина экспорта: в сети нет хранилища, поэтому экспортировать нечего.
  </BoxAnnotation>

<DiamondAnnotation pos="4.5 0.5 0.5" color="#ff0000">
        Источник
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 0.5" color="#ff0000">
        Пункт назначения
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Схема всего из шины импорта и шины экспорта работать не будет. Шина импорта попытается вытянуть предметы или жидкость из исходного инвентаря
и сохранить их в сетевом хранилище. Шина экспорта попытается вытянуть их из сетевого хранилища и положить
в принимающий инвентарь. Однако поскольку в этой сети **нет хранилища**, шина импорта не может импортировать,
а шина экспорта — экспортировать, так что ничего не происходит.

## Ввод и вывод через одну грань

Допустим, у вас есть машина, в которую можно подавать ресурсы и из которой можно забирать результат через одну и ту же грань (например, «<ItemLink id="charger" />»).
Вы можете и закладывать ингредиенты, и забирать результат, если объединить два способа с подсетями-трубами:

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/import_storage_export_pipe.snbt" />

<BoxAnnotation color="#dddddd" min="4 1 1" max="5 1.3 2">
        (1) Шина импорта: можно настроить фильтр.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 1 1" max="3 1.3 2">
        (2) Шина хранения: можно настроить фильтр. Она (как и другие шины хранения, через которые вы хотите и подавать, и забирать предметы)
        должна быть единственным хранилищем в сети.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 0 1" max="3 1 2">
        (3) Объект, в который вы хотите подавать и из которого забирать предметы: в данном случае зарядник.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 1 1" max="1 1.3 2">
        (4) Шина экспорта: фильтр обязателен.
  </BoxAnnotation>

<DiamondAnnotation pos="4.5 0.5 1.5" color="#00ff00">
        Источник
    </DiamondAnnotation>

<DiamondAnnotation pos="0.5 0.5 1.5" color="#00ff00">
        Пункт назначения
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Интерфейсы

Оказывается, помимо шин импорта и шин экспорта есть и другие [устройства](../ae2-mechanics/devices.md), которые помещают предметы в
[сетевое хранилище](../ae2-mechanics/import-export-storage.md) и извлекают их оттуда!
Здесь нас интересует «<ItemLink id="interface" />». Если в интерфейс вставить предмет, который он не настроен хранить в запасе, интерфейс
отправит его в сетевое хранилище, чем можно воспользоваться так же, как в трубе «шина импорта -> шина хранения». Если настроить интерфейс
на запас какого-то предмета, он будет вытягивать его из сетевого хранилища — как в трубе «шина хранения -> шина экспорта». Интерфейсу можно
задать запас для одних предметов и не задавать для других, что позволяет подавать и забирать предметы удалённо через шины хранения, если вам по какой-то причине это понадобится.

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/interface_pipes.snbt" />

<BoxAnnotation color="#dddddd" min="3.7 0 0" max="4 1 1">
        Интерфейс
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 1">
        Шина хранения
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3.7 0 2" max="4 1 3">
        Шина хранения
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 1 2" max="1 1.3 3">
        Интерфейс
  </BoxAnnotation>

<IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Один ко многим и многие к одному (и многие ко многим)

Конечно, вы не обязаны ограничиваться одной шиной «<ItemLink id="import_bus" />», «<ItemLink id="export_bus" />» или «<ItemLink id="storage_bus" />»

<GameScene zoom="3" background="transparent">
<ImportStructure src="../assets/assemblies/many_to_many_pipe.snbt" />

<IsometricCamera yaw="185" pitch="30" />
</GameScene>

## Подача в несколько мест

Из всего этого можно вывести способ отправлять ингредиенты с одной грани «<ItemLink id="pattern_provider" />» во множество разных
мест: например, в набор машин или на несколько разных граней одной машины.

Нам не подходят ни труба «импорт -> хранение», ни труба «хранение -> экспорт», потому что <ItemLink id="pattern_provider" /> на самом деле
никогда не содержит ингредиенты. Вместо этого поставщики *отправляют* ингредиенты в соседние инвентари, так что нам нужен
соседний инвентарь, который к тому же умеет импортировать предметы.

Похоже на... «<ItemLink id="interface" />»!
Убедитесь, что поставщик шаблонов находится в направленном или плоском режиме части и/или интерфейс находится в плоском режиме части, чтобы они не образовали сетевое
соединение.

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/provider_interface_storage.snbt" />

<BoxAnnotation color="#dddddd" min="2.7 0 1" max="3 1 2">
        Интерфейс (должен быть плоским, а не полным блоком)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 0 0" max="1.3 1 4">
        Шины хранения
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 0 0" max="1 1 4">
        Места, куда должен подавать поставщик шаблонов (несколько машин или несколько граней одной машины)
  </BoxAnnotation>

<IsometricCamera yaw="185" pitch="30" />
</GameScene>
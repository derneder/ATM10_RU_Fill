---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Специализированное локальное хранилище"
  icon: drive
---

# Специализированное локальное хранилище

Используя одно из [особых поведений интерфейса](../items-blocks-machines/interface.md#special-interactions),
[подсеть](../ae2-mechanics/subnetworks.md) может предоставить содержимое своего хранилища основной сети, при этом оставаясь
неспособной видеть хранилище основной сети и занимая всего 1 [канал](../ae2-mechanics/channels.md).

Это полезно для локального хранилища при какой-нибудь ферме: предметы не будут переполняться в ваше основное хранилище.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/local_storage.snbt" />

<BoxAnnotation color="#dddddd" min="4 0 0" max="5 2 1">
        (1) Какой-либо способ импорта предметов (в данном случае интерфейс)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 0 0" max="4 1 1">
        (2) Накопитель: внутри несколько ячеек. Ячейки должны быть размечены под то, что вырабатывает ферма.
        В ячейки можно установить карты равномерного распределения и пустотные карты.
        <Row><ItemImage id="item_storage_cell_4k" scale="2" /> <ItemImage id="equal_distribution_card" scale="2" /> <ItemImage id="void_card" scale="2" /></Row>
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="3 1 0" max="4 2 0.3">
        (3) Терминал изготовления: видит содержимое накопителя подсети, но не видит содержимого хранилища основной сети.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="2 0 0" max="2.3 1 1">
        (4) Интерфейс №2: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1.7 0 0" max="2 1 1">
        (5) Шина хранения: приоритет выше, чем у основного хранилища; может быть размечена под то, что вырабатывает ферма.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 2 0.3">
        Терминал изготовления: видит и содержимое хранилища основной сети, *и* содержимое подсети.
  </BoxAnnotation>

<DiamondAnnotation pos="0 0.5 0.5" color="#00ff00">
        В основную сеть
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

* Первый «<ItemLink id="interface" />» (1) просто принимает предметы с любой вашей фермы и выталкивает их в подсеть.
* «<ItemLink id="drive" />» (2) содержит несколько [ячеек](../items-blocks-machines/storage_cells.md). Ячейки должны быть
  [размечены](../items-blocks-machines/cell_workbench.md) под то, что вырабатывает ферма.
  В ячейки можно установить «<ItemLink id="equal_distribution_card" />» и «<ItemLink id="void_card" />».
* Второй «<ItemLink id="interface" />» (4) находится в конфигурации по умолчанию.
* «<ItemLink id="storage_bus" />» настроен с [приоритетом](../ae2-mechanics/import-export-storage.md#storage-priority)
  выше, чем у основного хранилища. Он может быть размечен под то, что вырабатывает ферма.

## Как это работает

* Интерфейс «<ItemLink id="interface" />» в подсети показывает шине хранения «<ItemLink id="storage_bus" />» основной сети содержимое
  накопителя «<ItemLink id="drive" />». Это значит, что шина хранения может напрямую забирать предметы из ячеек и помещать их туда обратно.
* Шина хранения настроена на высокий [приоритет](../ae2-mechanics/import-export-storage.md#storage-priority), чтобы предметы предпочтительнее
  возвращались в подсеть, а не в основное хранилище.
* Важно: если ячейки в подсети заполнятся, предметы не перельются в основную сеть. Если ферма ломается от остановки выгрузки,
  вместо этого можно использовать «<ItemLink id="void_card" />», чтобы удалять излишки.
* Если ферма вырабатывает несколько видов предметов, «<ItemLink id="equal_distribution_card" />» не даст одному предмету заполнить
  все ячейки и помешать хранению остальных.

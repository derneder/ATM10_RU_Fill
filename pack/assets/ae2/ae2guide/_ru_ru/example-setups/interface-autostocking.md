---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Автопополнение запасов через интерфейс"
  icon: interface
---

# Автопополнение запасов через интерфейс

Вы можете спросить: «Как поддерживать определённый запас разных предметов, изготавливая недостающее по мере необходимости?»

Одно из решений — <ItemLink id="interface" /> и <ItemLink id="crafting_card" />, которые автоматически запрашивают новые предметы
у [автокрафта](../ae2-mechanics/autocrafting.md) вашей сети. Эта схема лучше подходит для поддержания небольшого количества самых разных
предметов.

Эта демонстрационная схема урезана, чтобы не получилась слишком широкой; скорее всего, оптимально использовать 4 интерфейса «<ItemLink id="interface" />» и 4 шины «<ItemLink id="storage_bus" />»,
чтобы задействовать все 8 [каналов](../ae2-mechanics/channels.md) обычного [кабеля](../items-blocks-machines/cables.md).

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/interface_autostocking.snbt" />

<BoxAnnotation color="#dddddd" min="0 0 0" max="2 1 1">
        (1) Интерфейсы: настроены хранить нужные предметы в себе. В них стоят карты изготовления.
        <ItemImage id="crafting_card" scale="2" />
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 1 0" max="2 1.3 1">
        (2) Шины хранения: «Режим ввода/вывода» — «Только извлекать».
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

* Интерфейсы «<ItemLink id="interface" />» (1) настроены хранить нужные предметы в себе: нужный предмет кладётся кликом в их
   верхние слоты или перетаскивается туда из JEI, затем нажатием на значок гаечного ключа над слотами задаётся количество. В них стоят карты «<ItemLink id="crafting_card" />».
* Шины «<ItemLink id="storage_bus" />» (2) настроены так, что «Режим ввода/вывода» установлен на «Только извлекать».

## Как это работает

1. Если <ItemLink id="interface" /> не может получить из [сетевого хранилища](../ae2-mechanics/import-export-storage.md) достаточно настроенного предмета
   (и в нём стоит карта «<ItemLink id="crafting_card" />»), он запросит у [автокрафта](../ae2-mechanics/autocrafting.md) сети изготовление ещё этого предмета.
2. Шины «<ItemLink id="storage_bus" />» позволяют сети получать доступ к содержимому интерфейсов.
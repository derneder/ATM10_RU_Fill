---
navigation:
  parent: example-setups/example-setups-index.md
  title: "Автоматизация зарядника"
  icon: charger
---

# Автоматизация зарядника

Учтите: поскольку здесь используется <ItemLink id="pattern_provider" />, схема рассчитана на встраивание в вашу
систему [автокрафта](../ae2-mechanics/autocrafting.md). Если вам нужно просто автоматизировать <ItemLink id="charger" /> отдельно, используйте воронки, сундуки и тому подобное.

Автоматизировать <ItemLink id="charger" /> довольно просто. <ItemLink id="pattern_provider" /> проталкивает ингредиент в зарядник, а затем [подсеть-труба](pipe-subnet.md)
или другая предметная труба возвращает результат в поставщик.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/charger_automation.snbt" />

<BoxAnnotation color="#dddddd" min="1 0 0" max="2 1 1">
        (1) Поставщик шаблонов: в конфигурации по умолчанию, с соответствующими шаблонами обработки. Также снабжает зарядник энергией.

        ![Charger Pattern](../assets/diagrams/charger_pattern_small.png)
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="0 1 0" max="1 1.3 1">
        (2) Шина импорта: в конфигурации по умолчанию.
  </BoxAnnotation>

<BoxAnnotation color="#dddddd" min="1 1 0" max="2 1.3 1">
        (3) Шина хранения: в конфигурации по умолчанию.
  </BoxAnnotation>

<DiamondAnnotation pos="4 0.5 0.5" color="#00ff00">
        К основной МЭ-сети
    </DiamondAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Конфигурации

* <ItemLink id="pattern_provider" /> (1) находится в конфигурации по умолчанию, с соответствующими шаблонами «<ItemLink id="processing_pattern" />».
  Он же снабжает <ItemLink id="charger" /> [энергией](../ae2-mechanics/energy.md), потому что ведёт себя как [кабель](../items-blocks-machines/cables.md).
  
    ![Charger Pattern](../assets/diagrams/charger_pattern.png)

* <ItemLink id="import_bus" /> (2) находится в конфигурации по умолчанию.
* <ItemLink id="storage_bus" /> (3) находится в конфигурации по умолчанию.

## Как это работает

1. <ItemLink id="pattern_provider" /> проталкивает ингредиенты в <ItemLink id="charger" />.
2. Зарядник делает своё зарядное дело.
3. <ItemLink id="import_bus" /> в зелёной подсети вытягивает результат из зарядника и пытается поместить его в
   [сетевое хранилище](../ae2-mechanics/import-export-storage.md).
4. Единственное хранилище в зелёной подсети — <ItemLink id="storage_bus" />, которая помещает полученные предметы в поставщик шаблонов, возвращая их в основную МЭ-сеть.

---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "МЭ контроллер"
  icon: controller
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:controller
---

# МЭ контроллер

<BlockImage id="controller" p:state="online" scale="8" />

Контроллер — коммутационный узел [МЭ-сети](../ae2-mechanics/me-network-connections.md).
Без него сеть считается «ad-hoc» и может поддерживать всего максимум 8 использующих каналы
[устройств](../ae2-mechanics/devices.md).

Невозможно иметь 2 контроллера в одной [МЭ-сети](../ae2-mechanics/me-network-connections.md).

Контроллер даёт 32 [канала](../ae2-mechanics/channels.md) на каждую грань.

Контроллеру требуется 6 AE/t на каждый блок контроллера для работы. Каждый блок контроллера может хранить
8000 AE, так что для более крупных сетей может потребоваться дополнительное энергохранилище.
Подробности см. в разделе [энергия](../ae2-mechanics/energy.md).

Многоблочные контроллеры можно строить в довольно свободной форме.

<GameScene zoom="2" background="transparent">
  <ImportStructure src="../assets/assemblies/controllers.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Однако есть несколько правил, которые нужно соблюдать:

1.  Все блоки контроллера в [МЭ-сети](../ae2-mechanics/me-network-connections.md) должны быть соединены,
    иначе блоки покраснеют.
2.  Размер контроллера должен быть в пределах 7x7x7, иначе он покраснеет.
3.  У блока контроллера может быть 2 соседних блока максимум по 1 оси; если блок нарушает это правило,
    он отключится и покраснеет.

<GameScene zoom="2" background="transparent">
  <ImportStructure src="../assets/assemblies/controller_rules.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Пока все правила соблюдены и контроллер запитан, он должен светиться и переливаться цветами.

Можно щёлкнуть правой кнопкой мыши по контроллеру, чтобы получить тот же интерфейс, что у
<ItemLink id="network_tool" />.

## Рецепт

<RecipeFor id="controller" />

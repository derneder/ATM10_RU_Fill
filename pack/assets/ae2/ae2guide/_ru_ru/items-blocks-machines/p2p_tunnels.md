---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "P2P-тоннели"
  icon: me_p2p_tunnel
  position: 210
categories:
- devices
item_ids:
- ae2:me_p2p_tunnel
- ae2:redstone_p2p_tunnel
- ae2:item_p2p_tunnel
- ae2:fluid_p2p_tunnel
- ae2:fe_p2p_tunnel
- ae2:light_p2p_tunnel
---

# P2P-тоннели

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_tunnels.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

P2P-тоннели — способ перемещать предметы, жидкости, сигналы редстоуна, энергию, свет и [каналы](../ae2-mechanics/channels.md)
по сети, не взаимодействуя с ней напрямую. Существует множество разновидностей P2P-тоннелей, но каждая
переносит только свой конкретный тип содержимого. По сути они работают как порталы, напрямую соединяющие
грани двух блоков на расстоянии. Они не двунаправленны: у них чётко определены вход и выход.

![Портал](../assets/assemblies/p2p_portal.png)

Например, воронка, обращённая к предметному P2P-тоннелю, будет вести себя так, словно напрямую подключена к бочке, и предметы потекут.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_hopper_barrel.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Однако две бочки, стоящие рядом друг с другом, не будут передавать предметы друг другу.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_barrel_barrel.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Есть и другие разновидности, например редстоуновый P2P-тоннель.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_redstone.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

А также МЭ P2P-тоннель, переносящий каналы.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_channels.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Типы P2P-тоннелей и их настройка

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_tunnels.snbt" />
  <IsometricCamera yaw="180" pitch="90" />
</GameScene>

Существует множество типов P2P-тоннелей. Напрямую крафтится только МЭ P2P-тоннель, остальные получаются
щелчком правой кнопкой по другому P2P-тоннелю с определённым предметом в руке:
- МЭ P2P-тоннель выбирается щелчком правой кнопкой с любым [кабелем](../items-blocks-machines/cables.md).
- Редстоуновый P2P-тоннель выбирается щелчком правой кнопкой с любым из множества компонентов редстоуна.
- Предметный P2P-тоннель выбирается щелчком правой кнопкой с сундуком или воронкой.
- Жидкостный P2P-тоннель выбирается щелчком правой кнопкой с ведром или бутылочкой.
- Энергетический P2P-тоннель выбирается щелчком правой кнопкой почти с любым предметом, содержащим энергию.
- Светлый P2P-тоннель выбирается щелчком правой кнопкой с факелом или светокамнем.

У некоторых типов тоннелей есть особенности. Например, каналы МЭ P2P-тоннелей не могут проходить сквозь другие
МЭ P2P-тоннели, а энергетические P2P-тоннели косвенно взимают «налог» в 2,5% с проходящей через них энергии FE,
повышая собственное [потребление энергии](../ae2-mechanics/energy.md).

## Самая распространённая сфера применения P2P

Чаще всего P2P-тоннели используются для уплотнения передачи [каналов](../ae2-mechanics/channels.md) с помощью МЭ P2P-тоннеля.
Вместо пучка плотных кабелей множество каналов можно пропустить по одному плотному кабелю.

В этом примере 8 входов МЭ P2P-тоннелей принимают 256 каналов (8×32) от <ItemLink id="controller" /> основной сети,
а 8 выходов МЭ P2P-тоннелей передают их куда-то ещё. Обратите внимание: каждый вход или выход P2P-тоннеля
занимает 1 канал. Таким образом, по тонкому кабелю можно пропустить множество каналов. А поскольку наши
P2P-тоннели находятся в выделенной [подсети](../ae2-mechanics/subnetworks.md), на это даже не расходуются каналы
основной сети! Также заметьте: хотя P2P-тоннели можно ставить вплотную к контроллеру, между ними можно поставить
[плотный умный кабель](../items-blocks-machines/cables.md#smart-cable), чтобы удобнее видеть каналы.

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/p2p_compact_channels.snbt" />

  <BoxAnnotation color="#dddddd" min="1.3 1.3 6.3" max="2 2.7 6.7">
        Кварцевое волокно делит энергию между основной сетью и P2P-подсетью.
  </BoxAnnotation>

  <BoxAnnotation color="#dddddd" min="4.1 0 5.7" max="5 2.3 6.4">
        Вход тоннеля можно поставить прямо на контроллер или подключить к нему кабель.
  </BoxAnnotation>

  <IsometricCamera yaw="225" pitch="30" />
</GameScene>

Ещё один пример (включая использование с [квантовыми мостами](quantum_bridge.md)) — на этой схеме в MS Paint,
которую мне лень дорабатывать:

![P2P и квантовые мосты](../assets/diagrams/p2p_quantum_network.png)

## Вложенность

Однако таким способом нельзя пропустить бесконечное число каналов по одному кабелю. Канал МЭ P2P-тоннеля не
проходит сквозь другой МЭ P2P-тоннель, поэтому рекурсивно вкладывать их нельзя. Обратите внимание: внешний
слой МЭ P2P-тоннелей на красных кабелях отключён. Это ограничение действует только для МЭ P2P-тоннелей;
другие типы P2P-тоннелей могут проходить сквозь МЭ P2P-тоннель — например, редстоуновые P2P-тоннели
прекрасно работают.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_nesting.snbt" />
  <IsometricCamera yaw="225" pitch="30" />
</GameScene>

## Связывание

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_linking_frequency.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Концы соединения P2P-тоннеля можно связать с помощью <ItemLink id="memory_card" />. Частота отображается
в виде массива цветов 2×2 на задней стороне тоннеля.
- Щелчок правой кнопкой с зажатым Shift создаёт новую частоту связи P2P.
- Обычный щелчок правой кнопкой вставляет настройки, карты улучшений или частоту связи.

Тоннель, по которому вы щёлкнули с зажатым Shift, станет входом, а тоннель, по которому щёлкнули обычно, —
выходом. Выходов может быть несколько, но в МЭ P2P-тоннелях каналы, поступающие на вход, делятся между
выходами, так что дублировать каналы нельзя.

## Рецепт

<RecipeFor id="me_p2p_tunnel" />

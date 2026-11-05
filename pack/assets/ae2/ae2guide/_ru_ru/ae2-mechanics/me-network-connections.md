---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: "Сетевые подключения"
  icon: fluix_glass_cable
---

# Сетевые подключения

## Что значит «сеть»?

«Сеть» — это группа [устройств](../ae2-mechanics/devices.md), связанных блоками, которые умеют передавать [каналы](../ae2-mechanics/channels.md),
например [кабелями](../items-blocks-machines/cables.md) или машинами и [устройствами](../ae2-mechanics/devices.md) размером в целый блок. 
(<ItemLink id="charger" />, <ItemLink id="interface" />, <ItemLink id="drive" /> и т. д.)
Строго говоря, даже один-единственный кабель — это уже сеть.

## Небольшое отступление о расположении устройств

Для [устройств](../ae2-mechanics/devices.md) с конкретной сетевой функцией (например, <ItemLink id="interface" />,
который помещает предметы в [сетевое хранилище](../ae2-mechanics/import-export-storage.md) и извлекает их оттуда, <ItemLink id="level_emitter" />,
который считывает содержимое сетевого хранилища, или <ItemLink id="drive" />, который сам служит сетевым хранилищем, и т. п.)
физическое положение устройства не имеет значения.

Повторю: **физическое положение устройства не имеет значения**. Важно лишь, чтобы устройство было подключено к сети
(и, конечно, к какой именно).

## Сетевые подключения

Простой способ узнать, что подключено к сети, — воспользоваться предметом «<ItemLink id="network_tool" />». Он покажет все
компоненты сети, так что если вы видите лишнее или не видите нужного, значит, у вас проблема.

Например, здесь две отдельные сети.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/2_networks_1.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1 2 2">
        Сеть 1
  </BoxAnnotation>

<BoxAnnotation color="#5CA7CD" min="2 0 0" max="3 2 2">
        Сеть 2
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Здесь тоже две отдельные сети, потому что <ItemLink id="quartz_fiber" /> передаёт [энергию](../ae2-mechanics/energy.md),
не создавая сетевого подключения.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/2_networks_2.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1 2 2">
        Сеть 1
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="1.3 0 0" max="3 2 2">
        Сеть 2
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

А вот это всего одна сеть, а не две отдельные. [Квантовый сетевой мост](../items-blocks-machines/quantum_bridge.md) работает как
беспроводной [непрозрачный кабель](../items-blocks-machines/cables.md#dense-cable), поэтому оба конца находятся в одной сети.

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/actually_1_network.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="7 3 3">
        Всё — одна сеть
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Это тоже всего одна сеть: цвет [кабеля](../items-blocks-machines/cables.md) никак не влияет на сетевые подключения, кроме того, что кабели разных цветов не
соединяются друг с другом. Любые цвета соединяются с флюисовыми (или «бесцветными») кабелями.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/actually_1_network_2.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="4 2 2">
        Всё — одна сеть
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Подключения в контексте подсетей

[Подсети](../ae2-mechanics/subnetworks.md) используют сетевые подключения (а точнее, **ОТСУТСТВИЕ** подключения),
чтобы ограничить, какие [устройства](../ae2-mechanics/devices.md) имеют доступ к каким другим устройствам.

Подсеть — это, по сути, просто отдельная сеть.

Например, возьмём [автоматический фортунатор руды](../example-setups/ore-fortuner.md). Здесь три отдельные сети,
и каждая выполняет в установке свою задачу.

<GameScene zoom="6" interactive={true}>
  <ImportStructure src="../assets/assemblies/ore_fortuner.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 2" max="3 1 3">
        Сеть 1 работает как трубная подсеть: ограничивает доступ шины импорта, чтобы та «хранила» блоки руды через
        плоскости формирования.
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="0 0 0" max="3 1 1">
        Сеть 2 работает как ещё одна трубная подсеть: ограничивает доступ плоскостей уничтожения, чтобы те складывали
        руду, обработанную Удачей, в бочку, а не в вашу основную сеть. Это ещё и значит, что они не занимают каналы
        основной сети.
  </BoxAnnotation>

  <BoxAnnotation color="#82CD5C" min="2 0 1" max="4 1 2">
        Сеть 3 — основная сеть со всем вашим хранилищем и изготовлением. Здесь, по сути, только чтобы подавать питание, и при этом
        *не* подключена к двум подсетям.
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Подключения в контексте P2P

Один из вариантов [P2P-тоннеля](../items-blocks-machines/p2p_tunnels.md) переносит [каналы](channels.md) вместо предметов, жидкостей
или сигнала редстоуна, и почему-то это сбивает людей с толку. Сеть, к которой подключён тоннель, никак не связана с
сетью, которую он переносит. Это *могут* быть одна и та же сеть, но необязательно, и обычно это разные сети.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/p2p_channels_network_connection.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1.98 2 1">
        Сеть 1 — переносимая сеть (обычно ваша основная сеть)
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="2.02 0 0" max="3.98 1 1">
        Сеть 2 — сеть, в которой работают МЭ P2P-тоннели (обычно *не* ваша основная сеть)
  </BoxAnnotation>

  <BoxAnnotation color="#915dcd" min="4.02 0 0" max="6 1 1">
        Сеть 1 — переносимая сеть (обычно ваша основная сеть)
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

## Менее очевидные подключения

Здесь это всего одна сеть, потому что <ItemLink id="pattern_provider" />, будучи устройством размером в целый блок, работает как
кабель, и <ItemLink id="inscriber" /> делает то же самое. Поэтому сетевое подключение проходит сквозь
поставщик шаблонов и высекатель.

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/pattern_provider_network_connection_1.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="4 2 2">
        Всё — одна сеть
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Чтобы этого избежать (полезно во многих установках автокрафта с [подсетями](../ae2-mechanics/subnetworks.md)),
щёлкните по поставщику правой кнопкой мыши, держа предмет «<ItemLink id="certus_quartz_wrench" />»: он станет направленным и
не будет пропускать каналы через одну из сторон.

<Row gap="40">
<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/pattern_provider_network_connection_2.snbt" />

  <BoxAnnotation color="#915dcd" min="0 0 0" max="1.98 2 2">
        Сеть 1
  </BoxAnnotation>

  <BoxAnnotation color="#5CA7CD" min="2.02 0 0" max="4 2 2">
        Сеть 2
  </BoxAnnotation>

  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/pattern_provider_directional_connection.snbt" />

  <BoxAnnotation color="#ee3333" min="1 .3 .3" max="1.3 .7 .7">
        Обратите внимание: кабель не подключается
  </BoxAnnotation>

  <IsometricCamera yaw="255" pitch="30" />
</GameScene>
</Row>

Другие части, не создающие направленных сетевых подключений, — это большинство [устройств](../ae2-mechanics/devices.md), которые являются
[частями кабеля](../ae2-mechanics/cable-subparts.md), например «<ItemLink id="import_bus" />», «<ItemLink id="storage_bus" />» и
«<ItemLink id="cable_interface" />».

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/subpart_no_connection.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>
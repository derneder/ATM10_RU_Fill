---
navigation:
  parent: items-blocks-machines/items-blocks-machines-index.md
  title: "Кабели"
  icon: fluix_glass_cable
  position: 110
categories:
- network infrastructure
item_ids:
- ae2:white_glass_cable
- ae2:orange_glass_cable
- ae2:magenta_glass_cable
- ae2:light_blue_glass_cable
- ae2:yellow_glass_cable
- ae2:lime_glass_cable
- ae2:pink_glass_cable
- ae2:gray_glass_cable
- ae2:light_gray_glass_cable
- ae2:cyan_glass_cable
- ae2:purple_glass_cable
- ae2:blue_glass_cable
- ae2:brown_glass_cable
- ae2:green_glass_cable
- ae2:red_glass_cable
- ae2:black_glass_cable
- ae2:fluix_glass_cable
- ae2:white_covered_cable
- ae2:orange_covered_cable
- ae2:magenta_covered_cable
- ae2:light_blue_covered_cable
- ae2:yellow_covered_cable
- ae2:lime_covered_cable
- ae2:pink_covered_cable
- ae2:gray_covered_cable
- ae2:light_gray_covered_cable
- ae2:cyan_covered_cable
- ae2:purple_covered_cable
- ae2:blue_covered_cable
- ae2:brown_covered_cable
- ae2:green_covered_cable
- ae2:red_covered_cable
- ae2:black_covered_cable
- ae2:fluix_covered_cable
- ae2:white_covered_dense_cable
- ae2:orange_covered_dense_cable
- ae2:magenta_covered_dense_cable
- ae2:light_blue_covered_dense_cable
- ae2:yellow_covered_dense_cable
- ae2:lime_covered_dense_cable
- ae2:pink_covered_dense_cable
- ae2:gray_covered_dense_cable
- ae2:light_gray_covered_dense_cable
- ae2:cyan_covered_dense_cable
- ae2:purple_covered_dense_cable
- ae2:blue_covered_dense_cable
- ae2:brown_covered_dense_cable
- ae2:green_covered_dense_cable
- ae2:red_covered_dense_cable
- ae2:black_covered_dense_cable
- ae2:fluix_covered_dense_cable
- ae2:white_smart_cable
- ae2:orange_smart_cable
- ae2:magenta_smart_cable
- ae2:light_blue_smart_cable
- ae2:yellow_smart_cable
- ae2:lime_smart_cable
- ae2:pink_smart_cable
- ae2:gray_smart_cable
- ae2:light_gray_smart_cable
- ae2:cyan_smart_cable
- ae2:purple_smart_cable
- ae2:blue_smart_cable
- ae2:brown_smart_cable
- ae2:green_smart_cable
- ae2:red_smart_cable
- ae2:black_smart_cable
- ae2:fluix_smart_cable
- ae2:white_smart_dense_cable
- ae2:orange_smart_dense_cable
- ae2:magenta_smart_dense_cable
- ae2:light_blue_smart_dense_cable
- ae2:yellow_smart_dense_cable
- ae2:lime_smart_dense_cable
- ae2:pink_smart_dense_cable
- ae2:gray_smart_dense_cable
- ae2:light_gray_smart_dense_cable
- ae2:cyan_smart_dense_cable
- ae2:purple_smart_dense_cable
- ae2:blue_smart_dense_cable
- ae2:brown_smart_dense_cable
- ae2:green_smart_dense_cable
- ae2:red_smart_dense_cable
- ae2:black_smart_dense_cable
- ae2:fluix_smart_dense_cable
---

# Кабели

<GameScene zoom="3" background="transparent">
  <ImportStructure src="../assets/assemblies/cables.snbt" />
  <IsometricCamera yaw="180" pitch="30" />
</GameScene>

Хотя МЭ-сети также образуются соседствующими машинами с поддержкой МЭ, кабели — основной способ расширить
МЭ-сеть на большие расстояния.

Кабели разных цветов можно использовать, чтобы соседние кабели не соединялись друг с другом,
что позволяет эффективнее распределять [каналы](../ae2-mechanics/channels.md). Они также влияют на цвет подключённых
к ним терминалов, так что все ваши терминалы не обязаны быть фиолетовыми. Флюисовые кабели соединяются
с кабелями любого другого цвета.

Обратите внимание: **КАНАЛЫ НИКАК НЕ СВЯЗАНЫ С ЦВЕТОМ КАБЕЛЯ**

## Важное замечание

**Если вы новичок в AE2 и не знакомы с каналами, используйте умные кабели и непрозрачные умные кабели
везде, где возможно. Они показывают, как каналы проходят по вашей сети, и их поведение становится понятнее.**

## Ещё одно замечание

**Это не предметные, жидкостные, энергетические и т. п. трубы.** У них нет внутреннего инвентаря, поставщики шаблонов
и машины не «проталкивают» в них ничего — они лишь соединяют [устройства](../ae2-mechanics/devices.md) AE2 в сеть.

## Стеклянный кабель

<GameScene zoom="6" background="transparent">
<ImportStructure src="../assets/assemblies/fluix_glass_cable.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

<ItemLink id="fluix_glass_cable" /> — самый простой в крафте кабель: передаёт энергию
и до 8 [каналов](../ae2-mechanics/channels.md). Выпускается в 17 разных цветах, по умолчанию флюисовый,
и может быть окрашен в любой из 16 цветов.

Чтобы скрафтить цветные кабели, окружите краситель любого типа 8 кабелями одного типа (цвет кабелей не важен,
но тип должен совпадать: стеклянный, умный и т. д.). Также можно красить кабели в мире любой совместимой
с Forge кистью.

Любой цветной кабель можно скрафтить с ведром воды, чтобы смыть краску.

Кабель можно обернуть шерстью, чтобы получить <ItemLink id="fluix_covered_cable" />, а из <ItemLink id="fluix_smart_cable" /> можно
крафтовым путём узнать побольше о том, что происходит с вашими [каналами](../ae2-mechanics/channels.md).

<RecipeFor id="fluix_glass_cable" />

<RecipeFor id="blue_glass_cable" />

## Покрытый кабель

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/fluix_covered_cable.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Покрытый вариант кабеля не даёт никаких игровых преимуществ перед <ItemLink id="fluix_glass_cable" />. Однако его
можно использовать как альтернативный эстетический вариант, если вам больше нравится покрытый вид.

Можно красить так же, как <ItemLink id="fluix_glass_cable" />. Четыре <ItemLink id="fluix_covered_cable" /> можно скрафтить
с редстоуном и светокамнем, чтобы получить <ItemLink id="fluix_covered_dense_cable" />.

<Recipe id="network/cables/covered_fluix" />

<RecipeFor id="blue_covered_cable" />

## Непрозрачный кабель

<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/fluix_covered_dense_cable.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

Кабель большей ёмкости: в отличие от стандартного кабеля, который передаёт только 8 каналов, он передаёт 32 канала,
но не поддерживает шины, так что сначала нужно перейти с непрозрачного кабеля на кабель меньшего размера
(например, <ItemLink id="fluix_glass_cable" /> или <ItemLink id="fluix_smart_cable" />), и уже потом использовать шины
или плоскости.

Непрозрачные кабели немного перекрывают поведение каналов «кратчайший путь»: каналы сначала идут кратчайшим
путём к непрозрачному кабелю, а затем кратчайшим путём через этот непрозрачный кабель к контроллеру.

<Recipe id="network/cables/dense_covered_fluix" />

<RecipeFor id="blue_covered_dense_cable" />

## Умный кабель

<Row>
<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/fluix_smart_cable.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>
<GameScene zoom="6" background="transparent">
  <ImportStructure src="../assets/assemblies/fluix_smart_dense_cable.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>
</Row>

Хотя внешне они чем-то похожи на <ItemLink id="fluix_covered_cable" />, они дают диагностическую функцию,
визуализируя использование каналов на кабелях: каналы отображаются как светящиеся цветные линии, которые идут
вдоль чёрной полосы на кабеле, показывая, как используются каналы в вашей сети. На обычных умных кабелях
первые четыре канала показываются линиями цвета кабеля, а следующие четыре — белыми линиями. На непрозрачном
умном кабеле каждая полоса представляет 4 канала.

В сетях с <ItemLink id="controller" /> линии на кабелях показывают точный путь, по которому идут каналы.

В ad-hoc сетях умные кабели вместо этого показывают число каналов, используемых во всей сети, а не число каналов,
проходящих через конкретный кабель.

Их также можно красить так же, как <ItemLink id="fluix_glass_cable" />.

<Recipe id="network/cables/smart_fluix" />

<Recipe id="network/cables/dense_smart_fluix" />

<RecipeFor id="blue_smart_cable" />

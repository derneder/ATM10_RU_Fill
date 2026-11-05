---
navigation:
  title: "Дополнение: AE2 Import Export Card"
  icon: ae2importexportcard:export_card
  position: 150
categories:
  - tools
item_ids:
- ae2importexportcard:export_card
- ae2importexportcard:import_card
- ae2importexportcard:block_picker_card
---

# AE2 Import Export Card

<Row>
  <ItemImage id="ae2importexportcard:export_card" scale="2" />

  <ItemImage id="ae2importexportcard:import_card" scale="2" />

  <ItemImage id="ae2importexportcard:block_picker_card" scale="2" />
</Row>

Карты импорта, экспорта и выбора блока позволяют импортировать предметы из вашего инвентаря в сеть и экспортировать их из сети в инвентарь

## Карта импорта

<ItemImage id="ae2importexportcard:import_card" scale="2" />

Карта импорта берёт предметы из определённых слотов вашего инвентаря и сбрасывает их в вашу МЭ-систему.

![Import Card](diagrams/import_card.png)

Щелчок по слоту ставит в нём галочку. Любой предмет в слоте с галочкой будет импортирован в вашу МЭ-систему. Чтобы изменить фильтр, перетащите предметы из инвентаря в верхнюю часть окна.

### Улучшения

Карта импорта поддерживает следующие [улучшения](items-blocks-machines/upgrade_cards.md):

*   <ItemLink id="fuzzy_card" /> — фильтрация по уровню повреждения и/или игнорирование NBT предмета
*   <ItemLink id="inverter_card" /> — переключает фильтр с белого списка на чёрный

### Рецепт

<RecipeFor id="ae2importexportcard:import_card" />

## Карта экспорта

<ItemImage id="ae2importexportcard:export_card" scale="2" />

Карта экспорта работает точно так же, но вытаскивает предметы из вашей МЭ-системы в ваш инвентарь.

![Export Card](diagrams/export_card.png)

Чтобы указать нужные предметы, перетащите предмет из инвентаря в один из слотов вверху и щёлкните по слоту в вашем инвентаре, чтобы задать нужное число. Щелчок правой кнопкой мыши сбрасывает значение обратно на X.

### Улучшения

Карта экспорта поддерживает следующие [улучшения](items-blocks-machines/upgrade_cards.md):

*   <ItemLink id="fuzzy_card" /> — фильтрация по уровню повреждения и/или игнорирование NBT предмета
*   <ItemLink id="speed_card" /> — увеличивает скорость передачи с 1 предмета до целой стопки
*   <ItemLink id="crafting_card" /> — автоматически запрашивает и изготавливает предметы, которых сейчас нет в наличии

### Рецепт

<RecipeFor id="ae2importexportcard:export_card" />

## Карта выбора блока

<ItemImage id="ae2importexportcard:block_picker_card" scale="2" />

Карта выбора блока позволяет извлечь блок, на который вы сейчас смотрите, прямо из вашей сети. Просто наведитесь на блок и нажмите клавишу «Выбор блока». Если подходящий блок есть в вашей сети, он будет извлечён в ваш инвентарь.

![Block Picker Card](diagrams/block_picker_card.png)

### Рецепт

<RecipeFor id="ae2importexportcard:block_picker_card" />
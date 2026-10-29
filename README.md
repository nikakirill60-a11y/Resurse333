# Resurse333 — объединённый ресурс-пакет (RU) для Minecraft 1.21.11

Готовый пакет: **`Resurse333-merged-RU-1.21.11.zip`** (5,5 МБ, 3498 файлов).
Формат ресурс-паков: **75** (`pack_format: 75`, `min/max_format: [75, 0]`) — это Minecraft **1.21.11**.

Механизм переименования предметов в анвиле **удалён** — кастомные предметы
задаются через конфиг плагина (см. `items.yml`).

## Что внутри

В один пакет объединены все 7 исходных пакетов из этого репозитория:

| Исходный пакет | Что даёт | Автор |
|---|---|---|
| Blades of War 2 v2.1 | Модели и текстуры оружия (мечи, топоры, кирки, копья, луки, щиты) | Zerotekz |
| Blades Of Majestica | 119 моделей клинков | — |
| ALs-Mob-Weapons 1.3 | Особые модели оружия для мобов (работает без переименования — по типу сущности) | — |
| Dee's Extended Equipment | Доспехи, шлемы, инструменты-оружия (OptiFine CIT) | Deesaster_ + Vanilla Tweaks |
| Teyvat Weapon Collection 1.4.1 | Луки из Genshin Impact (OptiFine CIT) | Raycifer |
| More Hats 1.1 | Модели и текстуры 30 шлемов | Ililii_ и Hot_doggy13 |
| Somies Variable Hats | 45 шлемов (OptiFine CIT), с русскими названиями | Somies |

## Установка

1. Скопируйте `Resurse333-merged-RU-1.21.11.zip` в папку `resourcepacks`.
2. Включите пакет в списке ресурс-паков (для 1.21.11 предупреждений о версии быть не должно).
3. Для частей **Teyvat / Dee's / Somies** (OptiFine CIT) на 1.21.11 потребуется мод
   **CIT Resewn** (Fabric/Quilt) или OptiFine с поддержкой этой версии.
4. Логика оружия мобов (ALs-Mob-Weapons) встроена в пакет и работает **без модов**.

## Конфиг плагина — `items.yml` (заготовка)

В корне репозитория лежит **`items.yml`** — пример (заготовка) конфига кастомных
предметов: материал, название с цветами, лор, `custom-model-data`, зачарования и рецепт.

```yaml
items:
  ruby_sword:
    material: DIAMOND_SWORD
    name: '&c&lРубиновый меч'
    custom-model-data: 1001      # номер модели
    recipe:
      enabled: true
      shape: [' R ', ' R ', ' S ']
      ingredients: {R: REDSTONE_BLOCK, S: STICK}
```

- `custom-model-data: 1001` / `1002` — **заготовка**, показывающая формат:
  сюда подставляются номера ваших моделей.
- Когда в пакете появятся модели под эти номера, они подключаются селектом
  по `minecraft:custom_model_data` в соответствующем
  `assets/minecraft/items/<предмет>.json` (по аналогии с примером выше).

## Что было сделано при сборке

1. **Объединение** — все 7 паков слиты в один. Конфликтные файлы решены так:
   - 31 файл `assets/minecraft/items/*.json` — логика мобов ALs
     (`select` по `context_entity_type`) встроена как основная ветка,
     ванильная модель как запасная; дубликат `Cyber Katana` устранён;
   - `pack.mcmeta` — новый, формат 75 для 1.21.11, описание по-русски;
   - `pack.png` — обложка Blades of War 2;
   - `optifine/emissive.properties` — идентичен во всех паках;
   - `textures/misc/pumpkinblur.png` — полностью прозрачная версия (удобно для шлемов).
2. **Переименование убрано** — из 48 файлов `items/*.json` удалены все ветки,
   сопоставляющие модели по `custom_name` (и английские, и русские варианты);
   файл со списком названий удалён. Предметы теперь выдаются через плагин
   (см. `items.yml`).
3. **Русский язык сохранён там, где он не зависит от переименования**:
   описание пакета, `credits.txt`; в CIT-частях Teyvat (36) и Dee's (508 файлов)
   русские альтернативы regex-совпадений оставлены.
4. **Проверка** — все 1239 JSON валидны; 86 ссылок на модели проверены
   (17 отсутствующих — ванильные модели самого Minecraft: `bow_pulling_*`,
   `copper_*`, `mace`, `*_spear_in_hand`…).

## Особенности и ограничения

- `items.yml` — заготовка формата: `custom-model-data: 1001/1002` пока **не привязаны**
  к моделям в пакете (подключите их, когда появятся ваши модели).
- Части OptiFine-CIT (Dee's, Teyvat, Somies) сохранены со своими внутренними
  правилами сопоставления .properties — они не относятся к анвиль-механике пакета.
- Оригинальные zip-файлы пакетов сохранены в репозитории как есть.

## Кредиты

- Blades of War 2 — **Zerotekz**
- Dee's Extended Equipment — **Deesaster_**, короны от **Vanilla Tweaks** (vanillatweaks.net)
- Teyvat Weapon Collection — **Raycifer**
- More Hats — **Ililii_** и **Hot_doggy13**
- Blades Of Majestica, ALs-Mob-Weapons, Somies Variable Hats — авторы исходных пакетов

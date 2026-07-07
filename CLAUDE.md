# CLAUDE.md — ADB-control-panel-updater

Data-only репозиторий: хостит манифест обновлений для авто-апдейтера **ADB-control-panel**.
Кода здесь нет. Общение — на русском.

## Структура
- `version.json` — манифест: `{ "version": "X.Y.Z", "notes": "...", "url": "<GitHub Release .exe>" }`.
- `README.md` — заглушка.
- Бинарники релизов лежат в **GitHub Releases** этого репо (CDN), не в git.

## КРИТИЧНО
- **`version.json` НЕ править руками.** Он генерируется и пушится **CI из ADB-control-panel**
  (bump `APP_VERSION` в `config.py` → workflow собирает `.exe`, публикует Release и обновляет
  `version.json`). Ручная правка разъедется с реальным релизом.
- Текст release notes правится через **`RELEASE_NOTES`** в workflow ADB-control-panel, не здесь.

## Scope
- Человек/агент почти никогда не коммитит сюда напрямую — изменения приходят из upstream-пайплайна
  ADB-control-panel. Прямые правки — только по явной необходимости и с разрешения.
- Источник истины по версии/сборке — **[`../ADB-control-panel`](../ADB-control-panel)**.

## Заметка
- На момент написания `version.json` = `4.35.140`, тогда как приложение уже на 5.3.x — манифест
  **устарел**; чинить в upstream (прогнать релиз из ADB-control-panel), а не правкой этого файла.

> Общие правила — в корневом [`../CLAUDE.md`](../CLAUDE.md) и [`../WORK_RULES_PORTABLE.md`](../WORK_RULES_PORTABLE.md).

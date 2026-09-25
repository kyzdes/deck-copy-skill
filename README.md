# deck-copy

Движок текстов для презентаций: заголовки слайдов, тело, спикерские заметки, нарратив питча. Собран из шести deep-research отчётов — школы нарратива (Minto, Amazon narrative, инфостиль), разбор легендарных дек, наука восприятия слайда — и упакован из движка `copy-engine`.

Чем отличается от `clarity`: тот доводит до ясности любую русскую прозу, этот пишет текст деки по жанровому пресету и решает, сколько слов вообще имеет право быть на слайде.

## Что внутри

| Файл | Что там |
|---|---|
| `SKILL.md` | вход: носитель, шесть пресетов, процедура, стоп-правила, чек-лист сдачи |
| `references/method.md` | методика: выбор пресета, четырнадцать законов ядра с измерениями, процедура, русский слой |
| `references/presets.md` | шесть пресетов: голос, формулы заголовков, банк живых примеров, демо одного тезиса в шести жанрах |
| `references/linter.md` | правила с id для автопроверки и агента-линтера |
| `references/verdicts.md` | что измерено, что традиция, что опровергнуто |
| `references/matrix.md` | приёмы школ и чем они подтверждаются |
| `references/trench.md` | пресет «Окопный эксперт» развёрнуто, с разбором эталона |

## Порядок работы

1. Носитель: сцена, документ или гибрид. Тест — убери спикера.
2. Пресет из шести по таблице методики.
3. Скелет: все заголовки списком, titles-test.
4. Тело по законам ядра, лишнее — в спикерские заметки.
5. Вслух и русский слой.
6. Линт по правилам с id.

## Установка

```
claude plugin marketplace update claude-skills
claude plugin install deck-copy@claude-skills
```

Codex:

```
codex plugin marketplace upgrade
codex plugin add deck-copy@claude-skills
```

## Границы

Общая ясность русской прозы — плагин `clarity`: статьи, письма, README, доки. Вёрстка слайдов, шаблоны, шрифты, диаграммы и перевод деки — тоже не сюда: движок отвечает только за текст. Листинг App Store — плагин `aso`. Исходники движка (промпты, отчёты, дайджесты) лежат в `~/Desktop/Projects/skills/copy-engine` и нужны только для пересборки.

---

Личный маркетплейс: [kyzdes/claude-skills](https://github.com/kyzdes/claude-skills)

## Plugin update policy

When Claude's native auto-update is enabled for `claude-skills`, the host owns
updates and this plugin's fallback updater does no work. Native auto-update is
an independent user setting; hook environment flags do not disable it.

With native auto-update off, the fallback hook updates **only this plugin**,
in the background, at most once per four hours after a successful update.
Updates share an OS lock, have bounded command timeouts, and retry failed work
without starting a four-hour success cooldown. Set `KKZ_NO_AUTOUPDATE=1` to
disable the fallback; `KKZ_AUTO_UPDATE_INTERVAL_SEC` sets its cooldown.
Keys Keeper's fallback additionally requires `KEYS_KEEPER_ENABLE_MUTABLE_AUTOUPDATE=1`
and respects `KEYS_KEEPER_NO_AUTOUPDATE`. It never updates another plugin.
To prohibit every automatic update, disable native auto-update as well.
Logs contain operation names and exit codes only, under
`~/.cache/kyzdes-claude-skills/v2/<config-id>/`, isolated by Claude configuration.
Python 3.9 or newer is required for the fallback.

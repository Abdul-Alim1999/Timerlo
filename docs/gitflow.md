# Git Flow — Timerlo

## Основные ветки

- **`main`** — стабильный код, деплой в прод.
- **`develop`** — интеграционная ветка, деплой на тест/стейдж.
- **feature/fix/chore/docs/refactor** — рабочие ветки, создаются от `develop`, мержатся обратно в `develop`.

---

## Типы веток

| Тип ветки | Префикс | Пример |
| --- | --- | --- |
| Фича | `feat/` | `feat/timer-ui` |
| Багфикс | `fix/` | `fix/login-redirect` |
| Рефакторинг | `refactor/` | `refactor/session-service` |
| Обслуживание | `chore/` | `chore/update-deps` |
| Документация | `docs/` | `docs/gitflow` |

---

## Conventional Commits

Мы используем соглашение [Conventional Commits](https://www.conventionalcommits.org/).

| Тип | Когда использовать | Пример |
| --- | --- | --- |
| `feat:` | новая фича | `feat(timer): добавил UI таймера` |
| `fix:` | исправление бага | `fix(auth): починил редирект` |
| `chore:` | обслуживание (зависимости, конфиг) | `chore: обновил eslint` |
| `docs:` | изменения только в документации | `docs: добавил gitflow` |
| `refactor:` | улучшение кода без изменения поведения | `refactor: упростил хук useTimer` |
| `test:` | добавление или изменение тестов | `test: покрытие таймера unit-тестами` |
| `style:` | правки форматирования/стиля | `style: отформатировал код` |

---

## Правила работы с задачами

1. Берём Issue в GitHub Projects и назначаем себя.
2. Создаём ветку от `develop`:
    
    ```bash
    git checkout develop
    git pull origin develop
    git checkout -b feat/my-feature
    
    ```
    
3. Коммитим по Conventional Commits.
4. Пушим ветку и создаём **Pull Request в `develop`**
    1. В названии: `[#12] feat(timer): UI таймера`
    2. В описании — что сделано + скриншоты (если UI)
    3. Привязываем задачу: `closes #12`

---

## Code Review и Merge

- Минимум **1 аппрув** от коллеги.
- Прямые пуши в `main` и `develop` запрещены.
- Конфликты решает автор ветки.
- Мелкие правки — squash merge.
- Крупные фичи — merge commit.

---

## Релизы

- Мерж `develop` → `main` = релиз.
- Перед релизом создаём тег:
    
    ```bash
    git checkout main
    git pull origin main
    git tag -a v1.0.0 -m "First release"
    git push origin v1.0.0
    ```
    

---

## Чеклист перед PR

- [ ]  Локально проходит `pnpm lint && pnpm typecheck && pnpm build`
- [ ]  Удалены `console.log`
- [ ]  Скрины/видео UI приложены
- [ ]  Issue закрывается через `closes #ID`
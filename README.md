# Vite React Boilerplate - Завдання

## Зміст

- [Початкова підготовка середовища](#початкова-підготовка-середовища)
- [Аналіз структури файлу package.json](#аналіз-структури-файлу-packagejson)
- [Семантичне версіонування (SemVer)](#семантичне-версіонування-semver)
- [Дослідження додаткових конфігураційних файлів](#дослідження-додаткових-конфігураційних-файлів)
- [Аналіз роботи гіт-хуків Husky](#аналіз-роботи-гіт-хуків-husky)
- [Використання змінних оточення](#використання-змінних-оточення)

## Початкова підготовка середовища

1. Склонуйте репозиторій `vite-react-boilerplate`.
2. Встановіть усі залежності проєкту:
   ```bash
   pnpm install
   ```
3. Запустіть початковий скрипт сетапу проєкту:
   ```bash
   pnpm run setup
   ```

## Аналіз структури файлу package.json

1. Опишіть призначення полів файлу `package.json`:
   - **`name`**: Ім'я проєкту, унікальне для npm.
- **`author`**: Інформація про автора (ім'я, email).
- **`description`**: Короткий опис проєкту.
- **`version`**: Версія проєкту у форматі SemVer (`MAJOR.MINOR.PATCH`).
- **`license`**: Ліцензія, що визначає умови використання коду.
- **`repository`**: Посилання на репозиторій (тип і URL).
- **`scripts`**: Команди для автоматизації задач (наприклад, `dev`, `build`).
- **`dependencies`**: Бібліотеки, необхідні для роботи проєкту в продакшені.
- **`devDependencies`**: Бібліотеки для розробки та тестування, не потрібні в продакшені.
2. Проаналізуйте залежності у `dependencies` та `devDependencies`, поясніть логіку їх класифікації.
  ### `dependencies`
Бібліотеки для роботи проєкту в продакшені:
- **UI та стан**: `react`, `react-dom`, `@tanstack/react-query`, `@tanstack/react-router`, `@tanstack/react-table`, `react-hook-form`, `@hookform/resolvers`, `zustand` — для інтерфейсу, маршрутизації, таблиць, форм, управління станом.
- **Графіки**: `@nivo/bar`, `@nivo/core`, `@nivo/line`, `@nivo/pie` — візуалізація даних.
- **Локалізація та утиліти**: `i18next`, `i18next-browser-languagedetector`, `i18next-http-backend`, `react-i18next`, `dayjs`, `zod` — переклади, дати, валідація.

### `devDependencies`
Інструменти для розробки та тестування:
- **Сборка**: `vite`, `@vitejs/plugin-react-swc`, `typescript`, `postcss`, `tailwindcss` — збірка та стилі.
- **Лінтинг/форматування**: `eslint`, `prettier`, `@typescript-eslint/*` — перевірка та форматування коду.
- **Тестування**: `vitest`, `@playwright/test`, `@testing-library/*`, `@faker-js/faker` — юніт- та E2E-тести.
- **Storybook**: `storybook`, `@storybook/*` — розробка компонентів.
- **DevTools**: `@tanstack/*-devtools`, `@hookform/devtools` — відладка.
- **Контроль версій**: `husky`, `commitizen`, `@commitlint/*` — перевірка комітів.
- **UI для розробки**: `@headlessui/react`, `@heroicons/react` — компоненти та іконки.

### Логіка класифікації
- **`dependencies`**: Для функціональності проєкту в продакшені (UI, маршрутизація, графіки).
- **`devDependencies`**: Для розробки, тестування, збірки, не включаються в продакшен, щоб зменшити розмір збірки.

## Семантичне версіонування (SemVer)

1. Ознайомтесь із принципами SemVer.
2. Дослідіть версії пакетів бойлерплейту та поясніть, які оновлення (мажорні, мінорні, патчі) допускаються відповідно до версій у `package.json`.
   У `package.json` версії пакетів використовують SemVer (`MAJOR.MINOR.PATCH`) із префіксами `^` (дозволяє мінорні оновлення та патчі) або точними версіями (без оновлень).

### `dependencies`
- Усі з `^` (наприклад, `"react": "^18.3.1"`, `"zod": "^3.23.8"`):
  - **Допускаються**: мінорні (`18.4.x`) та патчі (`18.3.2`).
  - **Не допускаються**: мажорні (`19.0.0`).

### `devDependencies`
- З `^` (наприклад, `"eslint": "^9.9.1"`, `"typescript": "^5.5.4"`):
  - **Допускаються**: мінорні (`9.10.x`) та патчі (`9.9.2`).
  - **Не допускаються**: мажорні (`10.0.0`).
- Точні версії (наприклад, `"vite": "5.4.2"`, `"vitest": "2.0.5"`):
  - **Допускається**: лише вказана версія (`5.4.2`).
  - **Оновлення** (наприклад, `5.5.0`) потребує зміни `package.json`.

### Логіка
- `^`: Дозволяє нові функції та виправлення, зберігаючи сумісність (більшість пакетів).
- Точні версії: Фіксують критичні інструменти (`vite`, `vitest`) для стабільності.

## Дослідження додаткових конфігураційних файлів

Проаналізуйте та опишіть призначення, структуру та важливі елементи файлів:
### `README.md`
**Призначення**: Документація проєкту, що описує бойлерплейт, інструкції з налаштування, тестування, розгортання та пакети.

**Структура**:
- Заголовок, логотип, зміст.
- Розділи: Overview (технології), Requirements (Node.js 18+, pnpm), Getting Started (клонування, `pnpm install`, `pnpm run setup`), Important Note (Faker, структура), Testing (Vitest, Playwright), Deployment (з/без Docker), DevTools (TanStack, React Hook Form), Installed Packages (Base, UI, Testing тощо).

**Важливі елементи**:
- Інструкції для швидкого старту.
- Зауваження про Faker (локалізовані імпорти).
- Опис DevTools із умовним рендерингом.

### `.gitignore`
**Призначення**: Ігнорує непотрібні файли для Git (логи, збірки, тести, конфігурації редакторів).

**Структура**:
- Логи: `logs`, `*.log`.
- Залежності/збірки: `node_modules`, `dist`.
- Редактори: `.vscode/*` (крім `extensions.json`, `launch.json`), `.idea`, `.DS_Store`.
- Тести: `test-results/`, `coverage/`, `playwright-report/`.
- Storybook: `storybook-static`.

**Важливі елементи**:
- Виключення великих/особистих файлів.
- Винятки для `.vscode`.

### `LICENSE`
**Призначення**: Ліцензія MIT для вільного використання коду.

**Структура**:
- Назва: MIT License.
- Автор: Copyright (c) 2023 RicardoValdovinos.
- Умови: Дозволяє використання, модифікацію, поширення з вимогою збереження авторських прав.
- Відмова: Без гарантій, автор не несе відповідальності.

**Важливі елементи**:
- Простота MIT.
- Захист автора.
  

## Аналіз роботи гіт-хуків Husky

1. Дослідіть артефакти, які створюються після встановлення та налаштування бібліотеки Husky.
### Артефакти після встановлення Husky
- **Директорія `.husky/`**:
  - `husky.sh`: Основний скрипт для виконання хуків.
  - `prepare-commit-msg`: Викликає Commitizen (`npx cz`) для створення комітів.
  - `commit-msg`: Перевіряє формат комітів через Commitlint (`npx commitlint`).
  - `pre-commit`, `pre-push`, `post-merge` тощо: Шаблони хуків, порожні.
  - `.gitignore`: Зазвичай порожній.
  - `h`: Нестандартний, ймовірно, залишок.

2. Опишіть їх призначення, налаштування та роль у процесі розробки.
### Призначення, налаштування та роль
- **`husky.sh`**: Забезпечує сумісність хуків; додається автоматично (`npx husky init`).
- **`prepare-commit-msg`**: Запускає Commitizen для стандартизованих комітів; налаштовується в `package.json` (`"commitizen"`).
- **`commit-msg`**: Перевіряє формат комітів (Conventional Commits); налаштовується в `package.json` (`"commitlint"`).
- **`pre-commit`, `pre-push` тощо**: Для додаткових перевірок (наприклад, тестів); налаштовуються вручну.
- **`.gitignore`**: Ігнорує локальні файли; додається автоматично.
- **`h`**: Не використовується, ймовірно, зайвий.

**Роль у розробці**:
- Автоматизують перевірки (формати комітів, тести).
- Забезпечують єдиний стиль комітів.
- Покращують якість коду та командну роботу.
  
## Використання змінних оточення

1. Напишіть скрипт для читання довільної змінної оточення та виведення її значення у консоль.
<div align="center">
  <img src="https://github.com/volAndr1/Practice-2/blob/ec922fcbbe6dbe2a0d0476b1e20f838021cd240e/phpstorm64_EnplUvEU8l.png" alt="Скріншот проекту" width="500"/>
</div>
2. Задайте значення змінної на різних рівнях (ОС, сесія терміналу, окремий запуск скрипта, `.env` файл) та дослідіть пріоритетність їх застосування.
<div align="center">
  <img src="https://github.com/volAndr1/Practice-2/blob/5a8bf4f69bd383a4c45a9e98ec3b867b1b8d0257/SystemPropertiesAdvanced_bXosOdvzRV.png" alt="Скріншот проекту" width="500"/>
</div>
<div align="center">
  <img src="https://github.com/volAndr1/Practice-2/blob/5a8bf4f69bd383a4c45a9e98ec3b867b1b8d0257/phpstorm64_yNihsVpmLa.png" alt="Скріншот проекту" width="500"/>
</div>
<div align="center">
  <img src="https://github.com/volAndr1/Practice-2/blob/5a8bf4f69bd383a4c45a9e98ec3b867b1b8d0257/phpstorm64_OIqvykgKva.png" alt="Скріншот проекту" width="500"/>
</div>
<div align="center">
  <img src="https://github.com/volAndr1/Practice-2/blob/1166250a9449d89c8ccb7489a28a6171c39eff7f/phpstorm64_tfETAQVSYa.png" alt="Скріншот проекту" width="500"/>
</div>

# yanmus — патчи Morphe для Яндекс Музыки

Убирают телеметрию и рекламные трекеры. Подписку не обходят: нужен свой Плюс.

## Как пользоваться

Добавьте этот репозиторий как источник патчей в Morphe Manager: https://github.com/murikbmx/yanmus

<a href="https://morphe.software/add-source?github=murikbmx/yanmus">
  <img src=".github/assets/add-to-morphe.svg" alt="Add to Morphe" height="48">
</a>

Проверено на Яндекс Музыке 2026.11.1 (#171gpr).

| Патч | По умолчанию | Что делает |
|---|---|---|
| Disable AppMetrica | да | Не отправляет события, ошибки, сессии и местоположение в AppMetrica. Идентификаторы для входа в аккаунт работают |
| Disable AppsFlyer | да | Рекламный трекер AppsFlyer не запускается и не отправляет события |
| Disable Firebase telemetry | да | Флаги манифеста выключают Analytics, Crashlytics, Performance; удаляется разрешение AD_ID |
| Remove tracker components | нет | Экспериментально: удаляет из манифеста сервисы и ресиверы трекеров |

Push-уведомления Яндекса идут через AppMetrica Push, с патчем Disable AppMetrica они могут перестать приходить.

## После патча проверьте

- вход в аккаунт, воспроизведение, офлайн-кеш;
- что в логах нет отправок: `adb logcat | grep -iE "appmetrica|appsflyer|firebase"`.

## 🩹 Список патчей

<!-- PATCHES_START EXPANDED -->

<!-- Do not modify this section by hand. The patch list is generated when release.yml creates a new release.
     
     If you wish for the patches list to be collapsed, then remove the word 'EXPANDED' from the comment tag above.

     If you wish to manually keep this list updated then remove the PATCHES_START and PATCHES_END 
     comment blocks entirely. -->

#### A list of your patches will automatically be shown here after your first patches release is created.

&nbsp;

<!-- PATCHES_END -->

## Разработка

- Все изменения в ветку `dev`, стабильный релиз — слиянием `dev` в `main` (без squash).
- Сообщения коммитов: `feat:` (новая функция, minor), `fix:` (исправление, patch), `chore:` (без релиза).
- Релизы создаёт `release.yml` (semantic-release), вручную их не делать.
- Локальная сборка: `./gradlew :patches:buildAndroid` → `patches/build/libs/patches-*.mpp`
  (нужен GitHub-токен с `read:packages` в `gpr.user` / `gpr.key` или `GITHUB_ACTOR` / `GITHUB_TOKEN`).
